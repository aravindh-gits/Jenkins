pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout Code from GitHub'
                git branch: 'main', url: 'https://github.com/aravindh-gits/Jenkins.git'
            }
        }
        stage('Build Docker image') {
            steps {
                script{
                    echo 'Building Docker Image'
                    bat 'docker build -t aravindh077/dotnetapp .'
                    bat 'docker images'
                }
            }
        }
        stage('Push Docker image') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        echo 'Pushing docker image'
                        bat 'docker push aravindh077/dotnetapp'
                    }
                }
            }
        }
    }
}
