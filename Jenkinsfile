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

        stage('Build') {
            steps {
                echo 'No build step required for Node.js'
            }
        }

        stage('Use Secret') {
            steps {
                withCredentials([string(credentialsId: 'my-secret-token', variable: 'TOKEN')]) {
                    bat 'echo Secret token loaded successfully'
                    bat 'echo %TOKEN%'
                }
            }
        }

        stage('Run App') {
            steps {
                bat 'start /B node app.js'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}