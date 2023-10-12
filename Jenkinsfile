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
                sh 'cd webapp && curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - && sudo apt-get install -y nodejs && npm install && npm run build'
            }
        }
        stage('Release LMS') {
            steps {
                script {
                    echo 'Releasing..'
                    def packageJson = readJSON file: 'webapp/package.json'
                    def packageJSONVersion = packageJSON.version
                    echo "${packageJSONVersion}"
                    sh "sudo apt install zip && zip webapp/dist-${packageJSONVersion}.zip -r webapp/dist"
                    sh "curl -v -u admin:Omsrisai@78677 --upload-file webapp/dist-${packageJSONVersion}.zip http://20.219.51.51:8081/repository/lms/"
                }
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