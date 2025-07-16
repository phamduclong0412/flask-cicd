pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-cicd-app"
        CONTAINER_NAME = "flask-cicd-container"
    }

    stages {
        stage('Clone code') {
            steps {
                git branch: 'main', url: 'https://github.com/phamduclong0412/flask-cicd.git', credentialsId: 'github-pat'
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }

        stage('Run Docker container') {
            steps {
                script {
                    sh "docker rm -f $CONTAINER_NAME || true"
                    sh "docker run -d -p 5000:5000 --name $CONTAINER_NAME $IMAGE_NAME"
                }
            }
        }
    }
}

