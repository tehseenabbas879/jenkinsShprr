pipeline {
   
    agent any
  environment{
     DOCKERHUB_CREDENTIALS=credentials('dockerhub_211')
  }
    stages{
        stage('Build'){
            steps{
                bat 'npm install'

            }
        }
        stage('test'){
            steps{
                bat 'echo "Test is running"'
            }
        }
        stage('Docker build'){
            steps{
                bat 'docker build -t tehseenabbas211/jenkins-integration:latest .'
            }
        }
        stage('login'){
            steps{
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push'){
            steps{
                bat 'docker push tehseenabbas211/jenkins-integration:latest'
            }
        }
        stage('deploy'){
            steps{
                bat 'echo "Deploying the application"'
            }
        }
      
    }

}