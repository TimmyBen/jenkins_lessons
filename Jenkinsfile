// Tools allows you to have build tools available through the build tools attribute. Only gradle, maven and jdk are supported at the moment. These have to be set to use in Global Tool Configuration. 


pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('build') {
            steps {
                echo "building the application..."
            }
        }

        stage('test') {
            steps {
                echo "testing the application..."
            }
        }

        stage('deploy') {
            steps {
                echo "deploying the application..."
            }
        }
    }
}