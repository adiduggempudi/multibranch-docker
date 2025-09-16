pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 adinarayana25/service:bus'
            }
        }
        stage('Push'){
            steps{
                script{
                    withDockerRegistry(credentialsId: 'dockerhub-credientials') {
                           sh 'docker push adinarayana25/service:bus'
                     }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 adinarayana25/service:bus'
            }
        }
    }
}
