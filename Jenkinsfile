pipeline {
    agent any

    stages {

        stage('Code Checkout') {
            steps {
                git 'https://github.com/Aryan07CH/Amazon_Clone.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Docker Image Build') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true
                docker run -d -p 8080:8080 --name myapp myapp:latest
                '''
            }
        }
    }
}
