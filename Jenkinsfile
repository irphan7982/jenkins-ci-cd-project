pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-cred')  // Jenkins credentials ID
        DOCKER_IMAGE = 'irphan964/jenkins-ci-cd'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/irphan7982/jenkins-ci-cd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:latest", "./app")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        docker.image("${DOCKER_IMAGE}:latest").push()
                    }
                }
            }
        }

    post {
        success {
            echo '✅ CI/CD Pipeline executed successfully!'
        }
        failure {
            echo '❌ CI/CD Pipeline failed.'
        }
    }
}

