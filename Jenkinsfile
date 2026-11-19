
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
                sh 'docker build -t jenkins-demo:v1 .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker rm -f jenkins-demo || true'
                sh 'docker run -d --name jenkins-demo -p 8082:80 jenkins-demo:v1'
            }
        }

        stage('Verify') {
            steps {
                sh 'curl -f http://localhost:8082'
                echo 'Application is running!'
            }
        }

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
                        echo "Credentials loaded successfully"
                        echo "Password is protected"
                    '''
                }
            }
        }
    }
}

