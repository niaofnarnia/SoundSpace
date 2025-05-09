pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Intenta modificar los permisos del socket de Docker
                sh 'chmod 666 /var/run/docker.sock || true'
                sh 'docker build --no-cache -t soundspace .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker rm -f soundspace || true'
                sh 'docker run -d -p 8081:80 --name soundspace soundspace'
            }
        }
    }
}
