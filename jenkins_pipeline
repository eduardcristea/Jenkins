#!/usr/bin/env groovy
node {
    checkout scm 
    /* .. snip .. */
}
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'This is my first Jenkins Pipeline.'
            }
        }
        stage('Test') {
            steps {
                input ('Do you want to continue with the installation?')
            }
        }
        stage('Deploy') {
            parallel {
                stage('Deploy start') {
                    steps {
                        echo "Starting the deploy ....."
                    }
                }
                stage('Deploying now') {
                    agent {
                        docker {
                            reuseNode true
                            image 'node:latest'
                        }
                    }
                    steps {
                        echo "Docker Container with NODE Created"
                    }
                }
            }
        }
        stage('Prod') {
            steps {
                echo "Your application is ready"
            }
        }
    }
}
