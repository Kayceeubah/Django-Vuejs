pipeline {
    agent any
    stages {      
        stage('Docker build') {
                agent any
            steps {
                sh 'echo building'  
            }                                        
        }  
    }   
        stage('Docker push') {
                agent any
            steps {
                sh 'echo pushing'       
            }
        }
        stage('Deploy to Staging') {
                 agent any          
            steps {
                sshagent(credentials: ['server_ssh_key']) {
                   sh 'ssh -o StrictHostKeyChecking=no user@remote_server "cd project_directory && docker-compose up -d"'
                    }
            }
        }
}
