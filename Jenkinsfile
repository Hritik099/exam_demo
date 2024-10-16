pipeline {
    agent any  // Use any available agent
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code...'
                checkout scm  // Fetch the code from the GitHub repository
            }
        }
        stage('Build and Test') {
            steps {
                script {
                    echo 'Building the application inside Docker...'
                    // Run inside a Python Docker container
                    docker.image('python:3.8-alpine').inside {
                        sh 'python hello.py'  // Execute the Python "Hello World" script
                    }
                }
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
