pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop $(docker ps -q) || true
                docker rm $(docker ps -aq) || true
                docker run -d -p 80:80 devops-demo:v1
                '''
            }
        }
    }
}
