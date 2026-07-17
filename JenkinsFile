pipeline {
    agent any

    environment {
        IMAGE_NAME = "localhost:5000/orderservice"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build services/OrderService'
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                docker build \
                  -t ${IMAGE_NAME}:${BUILD_NUMBER} \
                  services/OrderService
                '''
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                docker push ${IMAGE_NAME}:${BUILD_NUMBER}
                '''
            }
        }
    }
}