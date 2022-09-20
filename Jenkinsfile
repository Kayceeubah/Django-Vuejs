pipeline {
    agent any
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
                withCredentials([
                    usernamePassword(credentials: 'dockerhub', usernameVariable: USER, passwordVariable: PWD)
                ])
                sh "docker login -u ${USER} -p ${PWD} && docker push gerrome/crud-vuejs-django_backend:1.2" 
                sh "docker login -u ${USER} -p ${PWD} && docker push gerrome/crud-vuejs-django_nginx:1.2"                            
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
