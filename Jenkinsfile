pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('dockerhub-credentials')  
        IMAGE_NAME = "shravani3001/flask-app"
    }

    stages {
        stage('Test GitHub Access') {
            steps {
                sh 'curl -I https://github.com || echo "GitHub not reachable"'
            }
        }

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/avigna3001/flask-app.git'
            }
        }

        stage('Test Docker Access') {
            steps {
                sh 'docker version || echo "Docker not accessible from Jenkins"'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh "echo $DOCKER_HUB_CREDENTIALS_PSW | docker login -u $DOCKER_HUB_CREDENTIALS_USR --password-stdin"
                    sh "docker push $IMAGE_NAME"
                }
            }
        }
    }
}


