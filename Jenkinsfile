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

        stage('Test Image') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'echo Container is healthy'
                    }
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        dockerImage.push("${IMAGE_TAG}")
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }

         post {
        success {
            echo 'Website Successfully Deployed to Apache Server'
        }

        failure {
            echo 'Deployment Failed'
        }
    }
}
