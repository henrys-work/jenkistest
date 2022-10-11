pipeline {
  
  environment {
    registry = "kildarejoe1/jenkinstest"
    registryCredential = 'dockerhub'
  }
  agent any

  }
  stages {
    stage('Create Docker Image') {
     steps {
       script { 
        docker.build registry + ":$BUILD_NUMBER"
       }
     }
  }
    stage('build') {
      steps {
        sh 'python --version'
      }
    }

    stage('test') {
      steps {
        sh 'echo Testing'
      }
    }

    stage('Deployment') {
      steps {
        sh 'echo Deploying to Production'
      }
    }

  }
}
