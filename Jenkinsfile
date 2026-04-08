pipeline {
    agent any

    stages {

        stage('Cleanup') {
            steps {
                sh '''
                docker stop jenkins-app || true
                docker rm jenkins-app || true
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                docker build -t jenkins-app .
                '''
            }
        }

        stage('Run') {
            steps {
                sh '''
                docker run -d -p 8090:80 --name jenkins-app jenkins-app
                '''
            }
        }
    }
}