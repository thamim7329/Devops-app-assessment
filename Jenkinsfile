pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker-compose -f Docker-compose.yml build'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'trivy image devops-app-assessment-backend:latest || true'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker-compose -f Docker-compose.yml up -d --build'
            }
        }

        stage('Verify Running Services') {
            steps {
                sh 'docker ps'
            }
        }
    }
}