pipeline {
    agent any

    stages {
        stage('pipeline test') {
            steps {
                git credentialsId: 'f8706eb8-fc14-4d63-978e-9b60ccb708bf', url: 'https://github.com/mkumargoh/server.git'
                sh 'ssh -o StrictHostKeyChecking=no manish@192.168.8.4'
		sh 'rsync -avh index.html manish@192.168.8.4:/var/www/html'
            }
        }
    }
}

