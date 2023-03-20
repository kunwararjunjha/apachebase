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

                
                stage('Run Docker Container') {
            steps {
                script {
                    docker.run('httpd', '-p 8080:80')
                }
            }
        }

}
}
}
}
