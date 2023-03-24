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
                  sh '''  ansible-playbook -i /var/lib/jenkins/workspace/Ansible_httpd/inventory  /var/lib/jenkins/workspace/Ansible_httpd/apache.yml -e "ansible_become_password=a"  --extra-vars "ansible_ssh_user=krarjunjha ansible_ssh_pass=a"  '''
                  
        
      
      }
    }
    }
}



