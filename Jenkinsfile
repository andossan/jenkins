pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SEU_USUARIO/SEU_REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                    echo "🔧 Construindo imagem Docker..."
                    docker compose build
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "🚀 Subindo containers..."
                    docker compose down
                    docker compose up -d
                '''
            }
        }
    }

    post {
        success {
            echo "✔ Deploy concluído com sucesso!"
        }
        failure {
            echo "❌ Falha no pipeline!"
        }
    }
}

