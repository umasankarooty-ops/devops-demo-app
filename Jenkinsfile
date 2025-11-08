pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/umasankarooty-ops/devops-demo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t devops-demo-app .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop and remove old container if exists
                    sh 'docker stop devops-demo-app || true'
                    sh 'docker rm devops-demo-app || true'
                    // Run new container
                    sh 'docker run -d --name devops-demo-app -p 9091:8080 devops-demo-app'
                }
            }
        }
    }
}
