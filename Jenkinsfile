pipeline {
    agent any

    stages {

        stage('sonaranalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run  --rm -e SONAR_HOST_URL="http://20.219.51.51:9000" -e SONAR_LOGIN="sqp_7c6f25aabf4e2244f35a81767bb4a14bd4e3b37a"  -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
            }
        }
        stage('Build') {
            steps { 
                echo 'Building..'
                sh 'cd webapp && npm install && npm run build'
            }
        }
        stage('release') {
            steps {
                echo 'Releasing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}