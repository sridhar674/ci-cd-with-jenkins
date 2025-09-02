pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = "docker-compose"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sridhar674/ci-cd-with-jenkins.git'
            }
        }

        stage('Build & Run Containers') {
            steps {
                sh "${DOCKER_COMPOSE} down || true"   // cleanup if something is running
                sh "${DOCKER_COMPOSE} build"
                sh "${DOCKER_COMPOSE} up -d"
            }
        }

        stage('Verify Services') {
            steps {
                script {
                    // Example: check frontend (React/Node on port 3000)
                    sh 'sleep 10'  // wait for containers to be up
                    sh 'curl -f http://localhost:3000 || exit 1'
                    
                    // Example: check backend (Spring Boot/Node/Java on port 8080)
                    sh 'curl -f http://localhost:8080 || exit 1'
                }
            }
        }

        stage('Cleanup') {
            steps {
                sh "${DOCKER_COMPOSE} down"
            }
        }
    }

    post {
        always {
            echo "Cleaning up after pipeline"
            sh "${DOCKER_COMPOSE} down || true"
        }
        success {
            echo "✅ Pipeline executed successfully!"
        }
        failure {
            echo "❌ Pipeline failed! Check logs above."
        }
    }
}

