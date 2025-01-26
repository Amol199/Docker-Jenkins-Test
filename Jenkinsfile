pipeline {
    agent any
    
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                script {
                    echo "Starting Docker container..."
                }
                sh '''
                   echo "Listing files before build:"
                   ls -la
                   echo "Node version:"
                   node --version
                   echo "npm version:"
                   npm --version
                   echo "Running npm ci..."
                   npm ci
                   echo "Running npm build..."
                   npm run build
                   echo "Listing files after build:"
                   ls -la
                '''
            }
        }
    }
}