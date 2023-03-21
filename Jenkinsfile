pipeline {
    agent any
    environment {
        DOCKER_TAG = "httpd:${BUILD_NUMBER}"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_TAG, '-f /var/lib/jenkins/workspace/Dockerfile .')
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                 def dockerContainer = dockerImage.run("-d --name my-apache-container -p 80:80 ${DOCKER_TAG}")
                }
            }
        }
    }
}
