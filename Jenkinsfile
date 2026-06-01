pipeline {
    agent any

    environment {
        DOCKER_HUB_REPO = 'ayushmain/myapp'
        IMAGE_TAG       = "${5}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ayushrana6396-cpu/my-node-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${DOCKER_HUB_REPO}:${IMAGE_TAG}")
                }
            }
        }
    }
