pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building my project...'
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing my project...'
                sh 'test -f index.html'
                echo 'HTML file exists. Test passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment stage completed!'
            }
        }
    }
}
