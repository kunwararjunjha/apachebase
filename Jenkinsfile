pipeline {
    agent any
    environment {
        BUILD_NUMBER = sh(script: 'echo ${BUILD_NUMBER}', returnStdout: true).trim()
        IMAGE_NAME = "my-apache-container:${BUILD_NUMBER}"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("-t ${IMAGE_NAME} -f /var/lib/jenkins/workspace/Dockerfile .")
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.run("-d --name my-apache-container-${BUILD_NUMBER} -p 80:80 ${IMAGE_NAME}")
                }
            }
        }
    }
}

