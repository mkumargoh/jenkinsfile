pipeline {
    agent any

    stages {
        stage('pipeline test') {
            steps {
                git credentialsId: 'f8706eb8-fc14-4d63-978e-9b60ccb708bf', url: 'https://github.com/mkumargoh/server.git'
                sh 'rsync index.html /var/www/html'
            }
        }
    }
}

