pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    def dockerImage = docker.build('my-apache-container', '-f /var/lib/jenkins/workspace/Dockerfile .')

                    // Run the Docker container
                    def dockerContainer = dockerImage.run('-p 80:80 -d --name my-apache-container')

                    // Print the container ID for reference
                    echo "Container ID: ${dockerContainer.id}"
                }
            }
        }
    }
}
