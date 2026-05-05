pipeline {
    agent any

    environment {
        IMAGE_NAME = "ammar86048/cicd_app"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/ammaransari/node_ci_cd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'ammar86048',
                    passwordVariable: 'Amm@r86048'
                )]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push $IMAGE_NAME'
                }
            }
        }
    }
}
