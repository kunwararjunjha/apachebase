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
        
         stage('Tag image') {
           
             steps {
                  script {
          def commitId = sh(returnStdout: true, script: 'git rev-parse --short HEAD').trim()
                    def imageName = "my-apache-container:${params.build_number}-${commitId}"
                    def containerName = "my-apache-container-${params.build_number}-${commitId}"
        // Tag the image with the Nexus repository URL
        sh 'docker tag my-apache-container:${params.build_number}-${commitId} localhost:8083/repository/apache_image/my-apache-container:${params.build_number}-${commitId}'
      }
             }            
    }

    stage('Push image') {
      steps {
        // Log in to the Nexus registry
        sh 'docker login --username "admin" --password "#Arjun1234" localhost:8083/repository/apache_image'

        // Push the tagged image to the Nexus registry
        sh 'docker push localhost:8083/repository/apache_image/my-apache-container:80-9745949'
          
                   
          // Log in to the Nexus registry
        sh 'docker login --username "admin" --password "#Arjun1234" localhost:8083/repository/apache_image'
          
        sh 'docker pull localhost:8083/repository/apache_image/my-apache-container:80-9745949'  
          
        sh 'docker run -d --name apachee -p 80:80 localhost:8083/repository/apache_image/my-apache-container:80-9745949'

      }
    }
    }
}



