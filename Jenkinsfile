pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = 'hayati'
        DOCKER_IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                   sh "docker.build("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}") -f Dockerfile ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker.image("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}").run('-p 8080:80 --name hayati') {
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
