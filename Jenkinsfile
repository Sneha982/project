pipeline {
    agent any
    tools {
        maven 'maven-3.6.3'
    }
    stages {
        stage("build jar") {
            steps {
                script {
                    echo "Building The Application"
                    sh 'mvn package'

                }
            }
        }

        stage("build image") {
            steps {
                script {
                    echo "Building The Image"
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
                        sh 'docker build -t snehagunda1/demoapp:calapp-1.0 .'
                        sh "docker login -u $USERNAME -p $PASSWORD"
                        sh ' docker push snehagunda1/demoapp:calapp-1.0'

                }
            }
        }
        }
        stage("Deploy") {
            steps {
                script {

                    echo "Deploying The Application"

                }
            }
        }

     }
