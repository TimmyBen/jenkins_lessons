
pipeline {
    agent any
    environment { // The environment variables defined here will be available for all the blocks in your pipeline
        NEW_VERSION = '1.2.0'
        SERVER_CREDENTIALS = credentials('server-credentials')  // The credentials and credentials binding are two plugins that allows you to use your Jenkins credentials inside your Jenkinsfile. It takes the credentials ID as an argument
    }
    stages {
        stage('build') {
            steps {
                echo "building the application"
                echo "building version ${NEW_VERSION}"  // This is an enviroment variable. 
            }
        }

        stage('test') {
            steps {
                echo "testing the application"
                echo "deploying with ${SERVER_CREDENTIALS}"
                withCredentials([               
                    usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD) 
                ]) {
                   sh "some script ${USER} ${PWD}"
                }
            }
        }

        stage('deploy') {
            steps {
                echo "deploying the application"
            }
        }
    }
}