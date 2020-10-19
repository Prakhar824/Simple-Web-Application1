pipeline {
  environment {
    registry = "prakhar824/sysprov"
    registryCredential = 'prakhar824'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/prakhar824/Simple-Web-Application1.git'
      }
    }
    stage('Build') {
       steps {
         sh 'docker build -t simple-web-application .'
       }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
