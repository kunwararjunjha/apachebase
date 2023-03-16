pipeline {
    agent {
        label 'ubuntu'
    }
    stages {
        stage('Build') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install -y apache2'
                sh 'sudo systemctl start apache2'
                sh 'sudo systemctl enable apache2'
                sh 'sudo chmod -R 777 /var/www/html'
                sh 'echo "<html><body><h1>Welcome to my custom web page!</h1></body></html>" > /var/www/html/index.html'
            }
        }
        stage('Test') {
            steps {
                sh 'curl http://localhost'
            }
        }
        stage('Deploy') {
            steps {
                // your deployment steps here
            }
        }
    }
}
