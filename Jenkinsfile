pipeline {
    agent any

    stages {

        stage('sonaranalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run  --rm -e SONAR_HOST_URL="http://20.219.51.51:9000" -e SONAR_LOGIN="sqp_65bafee20d6af7b0a49addbc0b96ac62976f9b0e"  -v ".:/usr/src" sonarsource/sonar-scanner-cli -S -Dsonar.projectKey=lms'
            }
        }
        stage('Build') {
            steps { 
                echo 'Building..'
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