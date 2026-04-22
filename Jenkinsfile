pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp"
        CONTAINER_NAME = "myapp-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                // Jenkins already knows your repo from SCM config
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                script {
                    sh """
                    docker stop $CONTAINER_NAME || true
                    docker rm $CONTAINER_NAME || true
                    """
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh "docker run -d -p 80:80 --name $CONTAINER_NAME $IMAGE_NAME"
                }
            }
        }
    }
}
