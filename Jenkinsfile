pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building Hello World application...'
                    bat 'npm install'
                    bat 'npm run build'
                }
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    bat 'docker build -t hello-world-app:latest .'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    bat 'npm test'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying Docker image...'
                    // Deployment steps, e.g., push to Docker registry or deploy to Kubernetes
                }
            }
        }
    }
    
    post {
        always {
            mail to: 'piyushkotadiya801@gmail.com',
                 subject: "Jenkins Build ${currentBuild.fullDisplayName}",
                 body: "Build result: ${currentBuild.currentResult}\n\nCheck console output at ${env.BUILD_URL}console"
        }
    }
}
