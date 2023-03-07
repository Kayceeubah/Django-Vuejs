pipeline {
    agent any
    environment {
        DHUB = credentials('dockerhub')
    }
    stages {      
        stage('Docker build') {
                agent any
            steps {
                sh 'echo building'  
            }                                        
        }  
            
        stage('Docker push') {
                agent any
            steps {
                sh 'echo pushing'       
            }
        }
        stage('Docker-compose deploy') {
                agent any
            steps {
                sh 'echo deploying'
            }  
        }          

    }
}
