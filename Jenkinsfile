pipeline {
    agent any

    stages {

        stage("Build Docker Image") {
            steps {
                script {
                    dockerapp = docker.build("warubert/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }

        stage("Push Docker image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                    }
                    dockerapp.push('latest', 'dockerhub')
                    dockerapp.push("${env.BUILD_ID}", 'dockerhub')
                }
            }
        }

    }
}