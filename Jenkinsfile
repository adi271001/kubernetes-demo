pipeline {
    agent any

    stages {
        stage('Install Docker') {
            steps {
                script {
                    echo 'Docker not found. Installing Docker...'
                    
                    // Update package list
                    sh 'apt-get update'
                    
                    // Install Docker
                    sh 'apt-get install -y docker.io'
                    
                    // Start Docker service
                    sh 'systemctl start docker'
                    
                    // Enable Docker to start on boot
                    sh 'systemctl enable docker'
                    
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
