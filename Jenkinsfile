pipeline {
  agent any
  stages {
    stage('Create Docker Image') {
      steps {
        sh 'docker build -t flask-app:latest .'
      }
    }
    

    stage('Unit testing of Application') {
      steps {
        sh 'echo Testing'
      }
    }

    stage('run docker container') {
      steps {
        sh 'docker run -p 5000:5000 --name flask-app7 -d flask-app'
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

   
    stage('Deployment to Heroku') {
      steps {
        sh 'echo Deploying to Production'
      }
    }

  }
  environment {
    registry = 'kildarejoe1/jenkinstest'
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
}
