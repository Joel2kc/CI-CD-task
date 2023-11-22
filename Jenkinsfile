pipeline {
    agent any

    environment {
        // Define environment variables if needed
        DOCKER_IMAGE_NAME = 'hayati'
        DOCKER_IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git
                script {
                    checkout scm
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.build("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}", "-f Dockerfile .")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                // Run the Docker container
                script {
                    docker.image("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}").withRun('-p 8080:80') {
                        // Any additional commands to run inside the Docker container
                        echo 'Docker container is running!'
                    }
                }
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
