pipeline {
    agent any
    parameters {
        string(name: 'BUILD_NUMBER', defaultValue: '', description: 'Build number for the Docker image tag')
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image with a tag based on the build number parameter
                    def dockerTag = "my-apache-container:${params.BUILD_NUMBER}"
                    docker.build(dockerTag, '-f /var/lib/jenkins/workspace/Dockerfile .')
                    
                    // Run the Docker container with the same tag and expose port 80
                    docker.run("--name my-apache-container -d -p 80:80 ${dockerTag}")
                }
            }
        }
    }
}
