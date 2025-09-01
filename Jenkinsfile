pipeline {
    agent {
        docker { image 'docker:20.10.16' args '-v /var/run/docker.sock:/var/run/docker.sock' }
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/ci-cd-demo.git'
            }
        }
        stage('Build Images') {
            steps {
                sh 'docker-compose build'
            }
        }
        stage('Run Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }
        stage('Test Backend') {
            steps {
                sh 'curl -f http://localhost:3000 || exit 1'
            }
        }
    }
    post {
        always {
            sh 'docker-compose down'
        }
    }
}

