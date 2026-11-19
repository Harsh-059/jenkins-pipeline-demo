
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
                echo 'Building application...'
                sh 'ls -l'
            }

steps {
            
stage('Credentials Demo') {
    steps {
        withCredentials([
            usernamePassword(
                credentialsId: 'practice-creds',
                usernameVariable: 'MY_USERNAME',
                passwordVariable: 'MY_PASSWORD'
            )
        ]) {
            sh '''
                echo "Username is available to Jenkins"
                echo "Credentials loaded successfully"
                echo "Password is protected and will not be printed"
            '''
        }
    }
}

        }

        stage('Test') {
            steps {
                echo 'Testing application...'
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

        stage('Docker Run') {
            steps {
                echo 'Starting Docker container...'
                sh 'docker rm -f jenkins-demo || true'
                sh 'docker run -d --name jenkins-demo -p 8082:80 jenkins-demo:v1'
            }
        }

        stage('Verify') {
            steps {
                echo 'Checking application...'
                sh 'curl -f http://localhost:8082'
                echo 'Application is running!'
            }
        }
    }
}

