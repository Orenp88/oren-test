pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
        IMAGE_NAME = "orenp88/oren_alpine"
    }
   
    stages {
        stage('Code Checkout') {
            steps {
                git url: 'https://github.com/Orenp88/oren-test.git', branch: 'main'
            }
        }
        stage('Docker Build'){
            steps{
                sh 'docker build -t ${IMAGE_NAME}:latest .'
            }
        }
        stage('Docker Tag'){
            steps{
                sh 'docker tag ${IMAGE_NAME}:latest ${IMAGE_NAME}:${BUILD_NUMBER}'
            }
        }
    }
}
