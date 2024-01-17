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
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'ThippuChaitu#2528', usernameVariable: 'chaitanyaveeksha')]) {
        	     sh "docker login -u $chaitanyaveeksha -p $ThippuChaitu#2528"
                 sh 'docker push chaitanyaveeksha/myimage:latest'
                }
            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
