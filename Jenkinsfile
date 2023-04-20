pipeline {
    agent any
    stages{
        stage('Code'){
            steps{
            git url: 'https://github.com/raoulcarnot/node-todo-application.git', branch: 'master'
            }
    }
        stage('Build'){
            steps{
            sh 'docker build -t raoulcarnot/nodetodo:latest .'
        }
    }
        stage('Push'){
            steps{
                withCredentials([string(credentialsId: 'dockerHub', variable: 'dockerHubpwd')]) {
                     sh "docker login -u raoulcarnot -p ${dockerhubpwd}"
                     sh 'docker push raoulcarnot/nodetodo:latest'
                }
            }
        }
    }
}
