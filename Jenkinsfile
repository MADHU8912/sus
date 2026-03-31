pipeline {
    agent any

    environment {
        IMAGE_NAME = "sus-app"
        CONTAINER_NAME = "sus-container"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Code already checked from GitHub'
            }
        }

        stage('Check Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker stop %CONTAINER_NAME% || echo Not running'
                bat 'docker rm %CONTAINER_NAME% || echo Not exists'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8080:80 --name %CONTAINER_NAME% %IMAGE_NAME%'
            }
        }

        stage('Test') {
            steps {
                bat 'echo SUS pipeline test success'
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS'
        }
        failure {
            echo 'Pipeline FAILED'
        }
    }
}