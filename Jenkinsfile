pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Install Python if not installed already (in case Docker is not being used)
                sh 'python3 --version || sudo apt-get install -y python3'
                // Ensure pip is installed
                sh 'python3 -m ensurepip --upgrade'
            }
        }
        stage('Test') {
            steps {
                // Run the Python Hello World script
                sh 'python3 hello.py'
            }
        }
    }
    post {
        always {
            // Archive logs or results if needed
            archiveArtifacts artifacts: '**/hello.py', allowEmptyArchive: true
        }
    }
}
