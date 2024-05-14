pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub_211')
    }
    stages {
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }
        stage('test') {
            steps {
                bat 'echo "Test is running"'
            }
        }
        stage('Docker build') {
            steps {
                bat 'docker build -t tehseenabbas211/jenkins-integration:latest .'
            }
        }
        stage('Login') {
            // Remove the --password flag
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub_211', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    bat 'docker login -u $USERNAME --password-stdin' // Use sh for shell script execution
                }
            }
        }
        stage('push') {
            steps {
                bat 'docker push tehseenabbas211/jenkins-integration:latest'
            }
        }
        stage('deploy') {
            steps {
                bat 'echo "Deploying the application"'
            }
        }
    }
}
