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

        stage('Deploy DEV') {
            when {
                branch 'dev'
            }
            steps {
                echo 'Deploying to DEV environment'
            }
        }

        stage('Deploy QA') {
            when {
                branch 'qa'
            }
            steps {
                echo 'Deploying to QA environment'
            }
        }

        stage('Deploy PROD') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to PRODUCTION environment'
            }
        }
    }
}