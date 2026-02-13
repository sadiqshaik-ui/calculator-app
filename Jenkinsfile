pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sadiqshaikarchents/calculator-app:v1 .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh '''
                echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
                docker push sadiqshaikarchents/calculator-app:v1
                '''
            }
        }
    }
}
