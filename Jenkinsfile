pipeline {
    agent any
    environment {
        DHUB = credentials('dockerhub')
    }
    stages {      
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
        stage('Docker-compose deploy') {
                agent any
            steps {
                sh 'docker stop crud2_nginx_1 && docker stop crud2_backend_1'
                sh 'docker-compose pull && docker-compose up -d'
            }  
        }          

    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
