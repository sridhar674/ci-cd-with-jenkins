pipeline {
    agent any

    stages {
        stage('Debug Workspace') {
            steps {
                echo "🔎 Checking Jenkins workspace contents..."
                sh 'pwd'
                sh 'ls -la'
                sh 'ls -la frontend || echo "⚠️ frontend folder not found"'
                sh 'ls -la backend || echo "⚠️ backend folder not found"'
            }
        }

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sridhar674/ci-cd-with-jenkins.git'
            }
        }

        stage('Build & Run Containers') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
        }

        stage('Verify Services') {
            steps {
                sh 'docker ps -a'
            }
        }
    }

    post {
        always {
            echo "🧹 Cleaning up after pipeline"
            sh 'docker-compose down || true'
        }
        failure {
            echo "❌ Pipeline failed! Check logs above."
        }
        success {
            echo "✅ Pipeline completed successfully!"
        }
    }
}

