
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the application...'
                sh 'test -f index.html'
                echo 'Test passed!'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t jenkins-demo:v1 .'
            }
        }
    }
}

