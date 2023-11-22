pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git
                script {
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                // Your build steps go here
                echo 'Building the project...'
            }
        }

        stage('Test') {
            steps {
                // Your test steps go here
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                // Your deployment steps go here
                echo 'Deploying the application...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Perform additional actions here if needed.'
        }
        failure {
            echo 'Pipeline failed! Notify or rollback actions can be added here.'
        }
    }
}

