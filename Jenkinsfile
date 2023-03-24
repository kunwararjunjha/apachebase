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
                  sh 'ansible-playbook -vvv /var/lib/jenkins/workspace/Ansible_httpd/wwww.yml  --extra-vars "ansible_become_password=a"'
                  
        
      
      }
    }
    }
}



