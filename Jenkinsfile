pipeline {
    agent any
    parameters {
        string(name: 'build_number', defaultValue: '', description: 'Specify build number')
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def imageName = "my-apache-container:${params.build_number}"
                    def containerName = "my-apache-container-${params.build_number}"
                    docker.build(imageName, '-f /var/lib/jenkins/workspace/Dockerfile .')
                   # docker.run(
                    #    '-d',
                    #    '--name', containerName,
                     #   '-p', '80:80',
                        imageName.toString()  // convert GString to plain string
                    )
                }
            }
        }
    }
}


