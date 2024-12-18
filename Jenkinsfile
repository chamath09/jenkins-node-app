pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/chamath09/jenkins-node-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || echo "No tests implemented yet"'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t your-dockerhub-username/nodejs-app:latest .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-credentials', url: '']) {
                    sh 'docker push your-dockerhub-username/nodejs-app:latest'
                }
            }
        }
    }
}
