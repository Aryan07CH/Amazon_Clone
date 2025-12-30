pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'dir'
                bat 'if not exist index.html exit 1'
            }
        }

        stage('Docker Image') {
            steps {
                bat "docker build -t amazon-clone:%BUILD_NUMBER% ."
            }
        }

        stage('Deploy to Dev') {
            steps {
                bat '''
                docker stop amazon-dev || exit 0
                docker rm amazon-dev || exit 0
                docker run -d -p 8081:80 --name amazon-dev amazon-clone:%BUILD_NUMBER%
                '''
            }
        }

        stage('Manual Approval') {
            steps {
                input message: 'Approve deployment to Production?',
                      ok: 'Deploy'
            }
        }

        stage('Deploy to Prod') {
            steps {
                bat '''
                docker stop amazon-prod || exit 0
                docker rm amazon-prod || exit 0
                docker run -d -p 81:80 --name amazon-prod amazon-clone:%BUILD_NUMBER%
                '''
            }
        }
    }
}
