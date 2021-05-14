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
                git credentialsId: 'manish_id', url: 'https://github.com/mkumargoh/server.git'

            }
        }
     stage('Deployment'){
        steps {
            script {
             // move the new changed
             //sh 'mv index.html /var/www/html'
             withCredentials([usernamePassword(credentialsId: 'manishid', passwordVariable: 'pass', usernameVariable: 'user')]) {
             remote.user = user
             remote.password = pass
             sshPut remote: remote, from: "index.html", into: "/var/www/html"
           
             }
            }
            }
        }
    }
}
