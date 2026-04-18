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
                bat 'docker build -t pipelinecode-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker rm -f pipelinecode-container || exit 0'
                bat 'docker run -d -p 3000:3000 --name pipelinecode-container pipelinecode-app'
            }
        }
    }

    post {
        success {
            echo 'Docker pipeline executed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}