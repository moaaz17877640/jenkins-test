pipeline {
    agent any

    stages {
        stage('preparation') {
            steps {
                git 'https://github.com/moaaz17877640/jenkins-test.git'
            }
        }
        stage('ci') {
            steps {
                 withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME' , passwordVariable: 'PASSWORD')]) {
                sh  'docker build . -t moazelmahi/jenkins:v1.1 '
               sh 'docker login -u ${USERNAME}  -p ${PASSWORD}' 
              sh ' docker push moazelmahi/jenkins:v1.1' 
              sh ' docker run -d -p 5000:8080 moazelmahi/jenkins:v1.1' 
                
                 }
            }
            
        }
       
    }
}
