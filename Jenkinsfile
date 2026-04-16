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

        stage('Run App') {
            steps {
                bat 'start /B node app.js'
            }
        }
    }
}