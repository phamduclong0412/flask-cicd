pipeline {
    agent any

    stages {
        stage('Clone code') {
            steps {
                git 'https://github.com/<your-username>/<repo-name>.git'
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Run Docker container') {
            steps {
                sh 'docker rm -f flask-app || true'
                sh 'docker run -d -p 5000:5000 --name flask-app flask-app'
            }
        }
    }
}
