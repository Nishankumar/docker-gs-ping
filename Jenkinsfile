pipeline {
    
    agent any 
    
    environment {
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
    
    stages {
        
        stage('Checkout'){
           steps {                
                url: 'https://github.com/iam-veeramalla/cicd-end-to-end',
                branch: 'main'
           }
        }

        stage('Build Docker'){
            steps{
                script{
                    sh '''
                    echo 'Buid Docker Image'
                    docker build -t abhishekf5/cicd-e2e:${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push the artifacts'){
           steps{
                script{
                    sh '''
                    echo 'Push to Repo'
                    docker push abhishekf5/cicd-e2e:${BUILD_NUMBER}
                    '''
                }
            }
        }            
        
        stage('Update K8S manifest & push to Repo'){
            steps {
                script{                    
                }
            }
        }
    }
}
