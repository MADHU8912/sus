pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Checking source code'
            }
        }

        stage('Check Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Report') {
            steps {
                bat 'echo Build successful > build-log.txt'
                bat 'type build-log.txt'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
        always {
            archiveArtifacts artifacts: '*.txt', fingerprint: true
        }
    }
}