pipeline {
    agent any
    parameters {
        string(name: 'build_number', defaultValue: '', description: 'Specify build number')
    }
    stages {
        
        
         stage('Tag image') {
           
             steps {
                  sh 'ansible-playbook -vvv /var/lib/jenkins/workspace/Ansible_httpd/apache.yml  --extra-vars "ansible_become_password=a"'
                  
        
      
      }
    }
    }
}



