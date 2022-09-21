pipeline {
    agent any
    environment {
        DHUB = credentials('dockerhub')
    }
    stages {
        stage('Remote SSH') {
                agent any
            steps {
                sh 'ssh -o StrictHostKeyChecking=no victor@192.168.56.107'  
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
