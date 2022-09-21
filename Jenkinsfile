pipeline {
    agent any
    environment {
        DHUB = credentials('dockerhub')
    }
    stages {
        
        def remote = [:]
        remote.name = 'node2'
        remote.host = 'https://3c44-129-56-51-209.eu.ngrok.io/'
        remote.user = 'victor'
        remote.password = 'Ifah6354!'
        remote.allowAnyHosts = true
        stage('Remote SSH') {
            sshCommand remote: remote, command: "ls -lrt"
            }
        
        stage('Docker build') {
                agent any
            steps {
                sh 'cd subscription-api && docker build -t gerrome/crud-vuejs-django_backend:1.2 .'
                sh 'cd subscription-app && docker build -t gerrome/crud-vuejs-django_nginx:1.2 .'  
            }                                        
        }  
            
        stage('Docker push') {
                agent any
            steps {
                sh 'docker login -u ${DHUB_USR} -p ${DHUB_PSW} && docker push gerrome/crud-vuejs-django_backend:1.2' 
                sh 'docker login -u ${DHUB_USR} -p ${DHUB_PSW} && docker push gerrome/crud-vuejs-django_nginx:1.2'                            
            }
        }
            
        stage('Deploy') {
            steps {
                echo "deploying stuff"
            }
        }

    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
