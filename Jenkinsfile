pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build and Run Containers') {
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