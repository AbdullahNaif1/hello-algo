pipeline {
    agent any
    
    environment {
        // Define environment variables here if needed
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git 'https://github.com/krahets/hello-algo.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build your project using Maven
                sh 'mvn clean package'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build a Docker image with your application
                sh 'docker build -t my-app-image .'
            }
        }
        
        stage('Deploy to Container') {
            steps {
                // Run a Docker container with your application
                sh 'docker run -d --name my-app-container -p 8080:8080 my-app-image'
            }
        }
    }
    
    post {
        success {
            // This block will be executed if the pipeline succeeds
            echo 'Pipeline succeeded. Your application is deployed in a Docker container.'
        }
        
        failure {
            // This block will be executed if the pipeline fails
            echo 'Pipeline failed. Deployment to Docker container was not successful.'
        }
    }
}
