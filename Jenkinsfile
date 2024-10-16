pipeline {
    agent {
        docker {
            image 'python:3.8-alpine'  // Using a lightweight Python Docker image
            label 'docker-agent'       // Optional label for specific agent
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build and Test') {
            steps {
                echo 'Building the application...'
                sh 'python hello.py'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/hello.py', allowEmptyArchive: true
            echo 'Pipeline finished. Done!'
        }
    }
}
