pipeline {
    agent any

    environment {
        IMAGE_NAME = "soundspace-app"
        DOCKER_USER = "niaofnarnia"
        IMAGE_VERSION = "v1.0"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_VERSION} ."
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Optional: Stop and remove any previous container
                    sh "docker rm -f soundspace-container || true"

                    // Run the new container
                    sh "docker run -d --name soundspace-container -p 8080:80 ${IMAGE_NAME}:${IMAGE_VERSION}"
                }
            }
        }
    }
}
