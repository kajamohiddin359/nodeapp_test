pipeline {
    agent {
        label 'Jenkins_Master'
    }
  

    stages {
        stage('SCM') {
            steps {
                git credentialsId: 'GitHubCreds', url: 'https://github.com/kajamohiddin359/nodeapp_test.git'
            }
        }
        stage('Build'){
            
        steps{
            sh 'whoami'
            sh 'docker build -t khaja359/nodeapp_test:2.0 .'
             }
                      }
                      
        stage('docker login'){
            steps{
                script{
                withCredentials([string(credentialsId: 'khaja359', variable: 'DockerHubCreds')]) {
                sh 'docker login -u khaja359 -p ${DockerHubCreds}'
                }
            }
            }
        }
       
        stage('Push image build'){
            steps{
                
                sh 'docker push khaja359/nodeapp_test:2.0'
                
                
            }
        }
    }
    post { 
        always {
        sh 'docker logout'   
    }
    }
    
}
