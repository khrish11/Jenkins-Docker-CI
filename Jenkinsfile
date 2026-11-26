
pipeline {
    agent any

    environment {
        DOCKER_PATH = 'C:\\Users\\STUDENT\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe'
        IMAGE_NAME = 'localhost:5000/abh-app'
    }

    stages {

        stage('1. Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('2. Application Build & Test') {
            steps {
                bat '"C:\\Users\\STUDENT\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" --version'
                bat '"C:\\Users\\STUDENT\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" app.py'
            }
        }

        stage('3. Build & Tag Docker Image') {
            steps {
                bat '"%DOCKER_PATH%" --version'
                bat '"%DOCKER_PATH%" build -t %IMAGE_NAME%:1.0 -t %IMAGE_NAME%:latest .'
            }
        }

        stage('4. Push Image to Registry') {
            steps {
                bat '"%DOCKER_PATH%" push %IMAGE_NAME%:1.0'
                bat '"%DOCKER_PATH%" push %IMAGE_NAME%:latest'
            }
        }
    }
}
