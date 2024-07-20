pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/PiyushKotadiya/hello-world.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Hello World application...'
                bat 'npm install'
                // Remove or update this line if no build step is required
                // bat 'npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t hello-world-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'docker run -d -p 80:80 hello-world-app'
            }
        }
    }

    post {
        always {
            mail to: 'piyushkotadiya801@gmail.com',
                 subject: "Pipeline Status: ${currentBuild.currentResult}",
                 body: "Pipeline ${currentBuild.fullDisplayName} finished with status: ${currentBuild.currentResult}"
        }
    }
}
