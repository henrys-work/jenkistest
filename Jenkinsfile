pipeline {
  agent any
  stages {
    stage('Create Docker Image') {
      steps {
        script {
          dockerImage = docker.build flask-app
        }

      }
    }

    stage('run docker container') {
      steps {
        sh 'docker run -p 5000:5000 --name flask-app -d flask-app'
      }
    }

    stage('Upload Docker Image to Docker Hub') {
      steps {
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }

      }
    }

    stage('Remove Unused docker image') {
      steps {
        sh "docker rmi $registry:$BUILD_NUMBER"
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
  environment {
    registry = 'kildarejoe1/jenkinstest'
    registryCredential = 'dockerhub'
  }
}