pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t tomaranmol1807/pipelinecode-app:latest .'
            }
        }

        stage('DockerHub Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                }
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push tomaranmol1807/pipelinecode-app:latest'
            }
        }

    }

    post {
        success {
            echo 'Image pushed to DockerHub successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}