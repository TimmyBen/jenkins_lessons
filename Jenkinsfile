CODE_CHANGES = getGitChanges() // getGitChanges() will be an external groovy script that checks if any changes have been made to the code 
pipeline {
    agent any
    stages {
        stage('build') {
             when {
                expression {
                    BRANCH_NAME == 'dev' && CODE_CHANGES == 'true' // The CODE_CHANGES variable could be one you defined yourself as seen above. 
                }
            }
            steps {
                echo "building the application..."
            }
        }

        stage('test') {
            when {
                expression {
                    BRANCH_NAME == 'dev' || BRANCH_NAME == 'master' //The BRANCH_NAME variable is an environment available out of the box. This stage will only excecute if the current branch is "dev" or "master" in this example. 
                }
            }
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