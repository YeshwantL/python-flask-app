pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/YeshwantL/python-flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t python-web-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop python-container || exit 0
                docker rm python-container || exit 0
                '''
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 5000:5000 --name python-container python-web-app'
            }
        }
    }
}