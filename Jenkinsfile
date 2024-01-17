pipeline {
    agent any
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/LondheShubham153/node-todo-cicd.git', branch: 'master' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t chaitanyaveeksha/myimage:latest'
            }
        }
        stage('Push'){
            steps{
               
    
        	     sh "docker login -u chaitanyaveeksha
                 sh 'docker push chaitanyaveeksha/myimage:latest'
                }
            }
        
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
