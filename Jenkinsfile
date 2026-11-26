pipeline {
    agent any

    environment {
        REGISTRY = "localhost:5000"
        IMAGE_NAME = "abh-app"
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
        script {
            def dockerPath = 'C:\\Users\\STUDENT\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe'

            bat "\"${dockerPath}\" --version"
            bat "\"${dockerPath}\" build -t localhost:5000/abh-app:7 -t localhost:5000/abh-app:latest ."
        }
    }
}
stage('4. Push Image to Registry') {
    steps {
        script {
            def dockerPath = 'C:\\Users\\STUDENT\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe'

            bat "\"${dockerPath}\" push localhost:5000/abh-app:7"
            bat "\"${dockerPath}\" push localhost:5000/abh-app:latest"
        }
    }
}
    post {
        success {
            echo "Pipeline succeeded! Image ${REGISTRY}/${IMAGE_NAME}:${BUILD_NUMBER} is available locally and in the registry."
        }
    }
}
