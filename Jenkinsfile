pipeline {
    agent any
    stages {      
        stage('Deploy to Staging') {
                 agent any          
            steps {
                sshagent(credentials: ['server_ssh_key']) {
                   sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.87.15.119 "touch test.txt"'
                    }
            }
        }
    }
}
