pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('sample-app')
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image('sample-app').inside {
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    kubectl.apply('-f deployment.yaml')
                }
            }
        }
    }
}
