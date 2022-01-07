// 1. Increment patch version in pom.xml 
// 2. Read new version from pom.xml
// 3. Put together a new Docker image and replace the name
// 4. Build App by Cleaning target folder and building .jar file 
// 5  Build Docker Image from Dockerfile 
// 6. Tag Image with repo-Url and name
// 7. Log in to Private Docker Repository 
// 8. Push to Private Docker Repository


// This auto-updates version number in built jar file by altering the build package manager. It also uses the name to build Docker commands. 




pipeline {
    agent any
    tools {
        maven "Maven"
    }
    stages {
        stage('increment version') {
            steps {
                script {
                    echo "incrementing the app version..."
                    sh "mvn build-helper:parse-version versions:set \
                    -DnewVersion=\\\${parsedVersion.majorVersion}.\\\${parsedVersion.minorVersion}.\\\${parsedVersion.nextIncrementalVersion} \ versions:commit"
                    def matcher = readFile('pom.xml') =~ '<version>(.+)</version>'
                    def version = matcher[0][1]
                    env.IMAGE_NAME = "$version-$BUILD_NUMBER"
                }
            }
        }

        stage('build app') {
            steps {
                script {
                    echo "building the application..."
                    sh "mvn clean package"
                }
            }
        }

        stage('build image') {
            steps {
                script {
                    echo "building the docker image..."
                    withCredentials([userNamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh "docker build -t nanajanashia/demo-app:$IMAGE_NAME ."
                        sh "echo $PASS | docker login -u $USER --password-stdin"
                        sh "docker push nanajanashia/demo-app:$IMAGE_NAME"
                    }       
                }
            }
        }

        stage('deploy') {
            steps {
                script {
                    echo "deploying the application..."
                }
            }
        }
    }
}