def remote = [:]
remote.name = 'test'
remote.host = '3.235.54.9'
remote.port = 22
remote.allowAnyHosts = true


pipeline {
    agent any

     stages {
        stage('Git Clone') {
            steps {
                // Get some code from a GitHub repository
                git credentialsId: 'f8706eb8-fc14-4d63-978e-9b60ccb708bf', url: 'https://github.com/mkumargoh/server.git'

            }
        }
     stage('Deployment'){
        steps {
            script {
             // move the new changed 
             sh '''
                echo "echo hello world" >> test.sh
                cat test.sh
             '''
             sh 'ls'
             withCredentials([usernamePassword(credentialsId: 'manishid', passwordVariable: 'pass', usernameVariable: 'user')]) {
             remote.user = user
             remote.password = pass
             sshPut remote: remote, from: "index.html", into: "/tmp"
             sshPut remote: remote, from: "test.sh", into: "/tmp"
             sshCommand remote: remote, command: "ls /var/www/html && chmod +x /tmp/test.sh"
             sshScript remote: remote, script: 'test.sh'
             }
            }
            }
        }
    }
}
