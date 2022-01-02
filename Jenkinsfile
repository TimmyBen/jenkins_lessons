// Branch based logic for multibranch pipeline


// Steps to configure a multibranch pipeline are:

// - Configure Branch Sources to "Git"
// - Add git url, credentials and add branch under Behaviours
// - Add Filter by name (with regular expressions)
// - Use .\* to denote you want to build all branches
// - Set Build Configuration to "By Jenkinsfile" and Script Path to JenkinsFile


pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                script {
                    echo "Testing the application"
                    echo "Executing pipeline for  branch BRANCH_NAME"
                }
            }
        }

        stage('build') {
            when {
                expression {
                    BRANCH_NAME == 'master'
                }
            }
            steps {
                script {
                    echo "Building the application"
                }
            }
        }

        stage('deploy') {
            when {
                expression {
                    BRANCH_NAME == 'master'
                }
            }
            steps {
                script {
                    echo "deploying the application"
                }
            }
        }
    }
}