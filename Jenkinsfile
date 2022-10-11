pipeline {
  agent {
    docker {
      image 'python:3.10.7-alpine'
    }

  }
  stages {
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