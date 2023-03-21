pipeline {
    agent any
    stages {
        stage('build maven') {
            parallel {
                            stage('Build Docker Image') {
            steps {
                        script {
                          docker.build('httpd', '-f /var/lib/jenkins/workspace/Dockerfile .')
                          

                }
    }
                                
}

   stage('Build Docker Image') {
            steps {
                script {
                    def image = docker.build('4b8b224e39a7')
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image('4b8b224e39a7').run('-p 80:80 -d --name my-apache-container')
                }
            }
        }             
              

}
}
}
}
