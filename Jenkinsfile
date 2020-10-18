pipeline {
  environment {
    registry = "saravanan1r/devsecops-training"
    registryCredential = "DevsecopsTraining"
    dockerImage = ''
  }
  agent any
  
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    
    stage('Push to DockerHub') {
      steps {
        script {
          docker.withRegistry('', registryCredential ) {
            docker.Imagepush()
          }
        }
      }
    }
       
    
    stage('Test Run') {
      steps {
        sh 'docker run -d $registry:$BUILD_NUMBER'
      }
    }
  } 
} 
