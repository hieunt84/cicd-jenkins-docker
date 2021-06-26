pipeline {
    agent any
    environment {
      registry = "happyit/myweb:1111"
    }

    stages {
        
        stage('Build image code version 2') {
          steps{
            script {
              dockerImage = docker.build registry
            }
          }
        }       

    }
}
