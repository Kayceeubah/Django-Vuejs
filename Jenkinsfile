pipeline {
    agent any
    stages {  
        stage('Build Images') {
            agent {
                docker { image 'docker:20.10.16-dind'}
            }    
            steps {
                sh 'cd backend-folder && docker build -t backend-image:tag .'
                sh 'cd frontend-folder && docker build -t frontend-image:tag .'
                withCredentials([
                    usernamePassword(credentials: 'dockerhub', usernameVariable: USER, passwordVariable: PWD)
                ])
                sh "docker login -u ${USER} -p ${PWD} && docker push backend-image:tag" 
                sh "docker login -u ${USER} -p ${PWD} && docker push frontend-image:tag"                  
            }                           
        }  
    }
}
