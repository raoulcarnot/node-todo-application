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
                withCredentials([usernamePassword(credentialsId: 'dockerHub' , passwordVariable: 'dockerHubPassword' , usernameVariable: 'dockerHubUser')]) {
                     sh 'docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}'
                     sh 'docker push raoulcarnot/nodetodo:latest'
                }
            }
        }
    }
}
