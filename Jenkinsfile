pipeline {
    agent any
    stages {
        stage('build maven') {
            parallel {
                            stage('Build Docker Image') {
            steps {
                        script {
                    sh '  RUN apt update  '
                    sh '  RUN apt install –y apache2   '
                    sh '  RUN apt install –y apache2-utils   '
                    sh ' RUN apt clean   '
                    sh '  EXPOSE 80  '
                    sh ' CMD [“apache2ctl”, “-D”, “FOREGROUND”] '
                }
    }
}


}
}
}
}
