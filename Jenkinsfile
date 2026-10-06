pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out Sourashtra Chatbot source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the Sourashtra Chatbot...'
                bat 'npm install'
                bat 'npm run build'
            }
        }

        stage('Test/Validate') {
            steps {
                echo 'Validating JavaScript files...'
                bat 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t sourashtra-chatbot:latest .'
            }
        }

        stage('Result') {
            steps {
                echo 'CI Pipeline completed successfully!'
                echo 'Sourashtra Chatbot Docker image created successfully.'
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESSFUL - CI Pipeline completed.'
        }

        failure {
            echo 'BUILD FAILED - Please check the Jenkins console output.'
        }
    }
}