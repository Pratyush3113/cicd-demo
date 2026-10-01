pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh '''
                    docker build -t cicd-demo:test .
                    docker run --rm cicd-demo:test pytest
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-demo:jenkins .'
            }
        }
    }
}
