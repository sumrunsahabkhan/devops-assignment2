pipeline {
    agent { label 'ubuntu3' }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/sumrunsahabkhan/devops-assignment2.git'
            }
        }

        stage('Build & Run Containers') {
            steps {
                sh 'sudo docker-compose down || true'
                sh 'sudo docker-compose up -d --build'
            }
        }

        stage('Verify Running Containers') {
            steps {
                sh 'sudo docker ps'
            }
        }

        stage('Show Logs') {
            steps {
                sh 'sudo docker-compose logs --tail=50'
            }
        }
    }

    post {
        success {
            echo "✅ CI Build Completed Successfully!"
        }
        failure {
            echo "❌ Build Failed. Check logs."
        }
    }
}
