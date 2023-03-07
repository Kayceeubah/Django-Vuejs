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
                   sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.87.15.119 "touch test.txt"'
                    }
            }
        }
}
