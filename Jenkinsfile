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
                withCredentials([usernamePassword(credentialsId: 'dckr_pat_YkZBFcZ9kLCTJqYi450j2roCXuA', passwordVariable: 'ThippuChaitu#2528', usernameVariable: 'chaitanyaveeksha')]) {
        	     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
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
