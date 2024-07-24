pipeline {
    agent any

    stages {
        stage('Install Docker') {
            when {
                // Run this stage only if Docker is not already installed
                expression { !sh(script: 'docker --version', returnStatus: true) == 0 }
            }
            steps {
                script {
                    echo 'Docker not found. Installing Docker...'
                    
                    // Update package list
                    sh 'sudo apt-get update'
                    
                    // Install Docker
                    sh 'sudo apt-get install -y docker.io'
                    
                    // Start Docker service
                    sh 'sudo systemctl start docker'
                    
                    // Enable Docker to start on boot
                    sh 'sudo systemctl enable docker'
                    
                    // Verify Docker installation
                    sh 'docker --version'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t sample-app .'
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment commands here
            }
        }
    }
}
