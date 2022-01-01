
pipeline {
    agent any
    parameter {
        // string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices; ['1.1.0', '1.2.0', '1.3.0'], descriptions: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage('build') {
            steps {
                echo "building the application..."
            }
        }

        stage('test') {
            when {
                expression {
                    params.executeTests                              // This gives us a checkbox for whether to choose to execute this stage
                }
            }
            steps {
                echo "testing the application..."
                echo "deploying version ${params.VERSION}"          //This allows us select a particuar version from a drop down to be used here
            }
        }

        stage('deploy') {
            steps {
                echo "deploying the application..."
            }
        }
    }
}