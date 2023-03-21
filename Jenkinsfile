pipeline {
    agent any
    environment {
        BUILD_NUMBER = "${BUILD_NUMBER}"
        CONTAINER_NAME = "my-apache-container-${BUILD_NUMBER}"
        IMAGE_NAME = "my-apache-image-${BUILD_NUMBER}"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(
                        "${IMAGE_NAME}", 
                        "--build-arg BUILD_NUMBER=${BUILD_NUMBER} -f /var/lib/jenkins/workspace/Dockerfile ."
                    )
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.run(
                        "${IMAGE_NAME}",
                        "--name ${CONTAINER_NAME} -p 80:80 -d"
                    )
                }
            }
        }
    }
}

