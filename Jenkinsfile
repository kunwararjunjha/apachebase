pipeline {
    agent any
    stages {
        stage('build maven') {
            parallel {
                            stage('Build Docker Image') {
            steps {
                      sh 'sudo apt-get update'
                sh 'sudo apt-get install -y apache2'
                sh 'sudo systemctl start apache2'
                sh 'sudo systemctl enable apache2'
                sh 'sudo chmod -R 777 /var/www/html'
                sh 'echo "<html><body><h1>Welcome to my kingdom!</h1></body></html>" > /var/www/html/index.html'
    }
}


}
}
}
}
