pipeline {
    agent any
    environment {
      registry = "happyit/myweb"
      dockerImage = ""
      registryCredential = 'dockerhub'
    }

    stages {
        
        stage('Build image') {
          steps{
            script {
              dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
          }
        }       

        stage('Push Image') {
          steps{
            script {
              docker.withRegistry( "", registryCredential ) {
                dockerImage.push()
              }
            }
          }
        }        

    }
}
