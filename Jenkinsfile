pipeline {
    agent any

    stages {
         stage('build') {
            steps {
                sh 'docker build -t nodejs .'
            }
        }
        stage('push') {
            steps {
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 682111399744.dkr.ecr.us-east-1.amazonaws.com'
                sh 'docker tag nodejs:latest 682111399744.dkr.ecr.us-east-1.amazonaws.com/nodejs:latest'
                sh 'docker push 682111399744.dkr.ecr.us-east-1.amazonaws.com/nodejs:latest'
            }
        }
        stage('deploy'){
            steps{
                sh 'docker run -d --name nodejs-app -p 8080:8081 682111399744.dkr.ecr.us-east-1.amazonaws.com/nodejs:latest'

    }
}
