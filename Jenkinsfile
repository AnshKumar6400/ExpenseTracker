pipeline {
    agent any

    stages {
        stage('Pull Latest Code') {
            steps {
                sh '''
                cd /home/ubuntu/ExpenseTracker
                git pull origin main
                '''
            }
        }

        stage('Build & Deploy Docker') {
            steps {
                sh '''
                cd /home/ubuntu/ExpenseTracker
                docker compose down
                docker compose up -d --build
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Docker deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}