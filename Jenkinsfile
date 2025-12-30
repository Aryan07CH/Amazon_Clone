pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build stage'
                // sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage'
                // sh 'mvn test'
            }
        }

        stage('Docker Image Build') {
            steps {
                echo 'Docker build stage'
                // sh 'docker build -t myapp:latest .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage'
            }
        }
    }
}
