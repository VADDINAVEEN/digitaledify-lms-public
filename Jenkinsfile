pipeline {
    agent any

    stages {
        
        stage('sonaranalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'sudo docker run  --rm -e SONAR_HOST_URL="http://20.219.51.51:9000" -e SONAR_LOGIN="sqp_e409c410fd65103eb94e480bb3159a13f48e1300"  -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
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