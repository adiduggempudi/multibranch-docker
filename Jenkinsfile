pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 adinarayana25/service:movie'
            }
        }
        stage ("Push") {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'dockerhub-credientials') {
                         sh 'docker push adinarayana25/service:movie'
                     }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 adinarayana25/service:movie'
            }
        }
    }
}
