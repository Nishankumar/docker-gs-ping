pipeline {
    
    agent any 
    
    environment {
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
    
    stages {
        
        stage('Checkout'){
           steps {                
               git url: 'https://github.com/Nishankumar/docker-gs-ping.git', branch: 'main'
           }
        }

        stage('Build Docker'){
            steps{
                script{
                    sh '''
                    echo 'Buid Docker Image'
                    docker build -t nishankumar1999/goapp:${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push the artifacts'){
           steps{
                script{
                    sh '''
                    echo 'Push to Repo'
                    def dockerImage = docker.image("nishankumar1999/goapp:${BUILD_NUMBER}")
                    docker.withRegistry('https://registry.hub.docker.com', "docker-cred") {
                    dockerImage.push()
                    }
                    '''
                }
            }
        }                    
    }
}
