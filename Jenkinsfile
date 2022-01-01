def gv 

pipeline {
    agent any
    parameter {
        // string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices; ['1.1.0', '1.2.0', '1.3.0'], descriptions: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage('init') {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage('build') {
            steps {
                script {
                    gv.buildApp()
                }
            }
        }

        stage('test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }
        }

        stage('deploy') {
           steps {
               input {
                   message "Select the environment to deploy to"
                   ok "Done"
                   parameters {
                       choice(name: 'ENV', choices; ['dev', 'staging', 'prod'], descriptions: '')
                   }
               }
                script {
                    gv.deployApp()
                    echo "Deploying to ${ENV}"
                }
            }
        }
    }
}

// NB: The parameter defined inside this stage is scoped to that stage. Declare it as a variable to use it anywhere else