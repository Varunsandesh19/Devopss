pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/Varunsandesh19/Devopss.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devopss-app .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f devopss-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name devopss-container devopss-app'
            }
        }
    }
}
