pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    docker run --rm \
                    -v "$PWD:/app" \
                    -w /app \
                    python:3.14-slim \
                    sh -c "pip install -r requirements.txt && pip install pytest && pytest"
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
