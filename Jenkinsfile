pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/AJEN17/NeuroBalance.git'
            }
        }
        
        stage('Tear Down Old Environment') {
            steps {
                sh 'docker compose down || true'
                sh 'docker network prune -f || true'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy Full Stack') {
            steps {
                sh 'docker compose up -d'
            }
        }
        
        stage('Verify Deployment') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
