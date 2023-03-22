pipeline {
    agent any
    parameters {
        string(name: 'build_number', defaultValue: '', description: 'Specify build number')
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def commitId = sh(returnStdout: true, script: 'git rev-parse --short HEAD').trim()
                    def imageName = "my-apache-container:${params.build_number}-${commitId}"
                    def containerName = "my-apache-container-${params.build_number}-${commitId}"
                    docker.build(imageName, '-f /var/lib/jenkins/workspace/Dockerfile .')
                }
            }
        }
        
        stage('Build and push image') {
            steps {
                sh 'docker build -t my-apache-container:${params.build_number}-${commitId} .'
                sh 'docker tag my-apache-container:${params.build_number}-${commitId} localhost:8083/repository/apache_image/my-apache-container:${params.build_number}-${commitId}'
                sh 'docker login localhost:8083/repository/apache_image -u admin -p #Arjun1234'
                sh 'docker push localhost:8083/repository/apache_image/my-apache-container:${params.build_number}-${commitId}'
            }
        }
    }
}



