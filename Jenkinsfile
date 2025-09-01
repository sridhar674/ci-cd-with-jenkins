pipeline {
    agent {
        docker {
            image 'docker:20.10.16'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sridhar674/ci-cd-with-jenkins.git'
            }
        }
        stage('Build & Run') {
            steps {
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
        }
        stage('Test') {
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

