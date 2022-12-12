pipeline {
    agent any

    stages {
        stage('cehckout') {
            steps {
                git branch: 'master', url: 'https://github.com/venky3690/venky3690.git'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t myimage .'
            }
        }
        stage('Publish Image to Docker Hub') {
            steps {
                withDockerRegistry([ credentialsId: "dockerHub", url: ""]) {
                   sh 'docker push myimage:latest'
            }
        }
        
        stage('Run Docker Container on jenkins Agent') {
            steps {
                
                  sh "docker run -dt -p 8080:8080 myimage"
            }
        }
    }
  
}
