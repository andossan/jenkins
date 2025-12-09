pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/andossan/jenkins.git',
                    branch: 'main',
                    credentialsId: 'github-token'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        failure {
            echo "❌ Falha no pipeline!"
        }
        success {
            echo "✅ Deploy concluído com sucesso!"
        }
    }
}

