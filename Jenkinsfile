
pipeline {
    agent any
    stages {
        stage('') {
            steps {
                echo "building the application..."
            }
        }

        stage('') {
            steps {
                echo "testing the application..."
            }
        }

        stage('') {
            steps {
                echo "deploying the application..."
            }
        }
    }
    post {   // Used to do some action after the original build sequence has exited. 
        always {
            // Do this action if the build stage succeeded
        }
        success {
            //
        }
        failure {
            //
        }
    }
}