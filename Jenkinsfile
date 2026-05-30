pipeline {
    agent any

    stages {
        
        stage('Test') {
            steps {
                echo 'Jenkins is working'
                sh 'whoami'
                sh 'pwd'
            }
        }

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ayushrana6396-cpu/my-node-app.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Started'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Deploy to Apache Server') {
            steps {
                echo 'Deploying Website to Apache'
                sh 'cp -r ./* /var/www/html/'
            }
        }

        stage('Verify Deployment') {
            steps {
                echo 'Checking Apache Directory'
                sh 'ls -la /var/www/html/'
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
