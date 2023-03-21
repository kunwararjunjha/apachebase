pipeline {
    agent any
    environment {
        IMAGE_NAME = "my-apache-container:${BUILD_NUMBER}"
        CONTAINER_NAME = "my-apache-container-${BUILD_NUMBER}"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image with a tag that includes the build number
                    docker.build("${IMAGE_NAME}", '-f /var/lib/jenkins/workspace/Dockerfile .')
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container with a name that includes the build number
                    docker.run("${IMAGE_NAME}", "--name ${CONTAINER_NAME} -d -p 80:80")
                }
            }
        }
    }
}
