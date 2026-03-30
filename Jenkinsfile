pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "yourdockerhub/devops-q1:latest"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/yourusername/devops-q1-app.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}