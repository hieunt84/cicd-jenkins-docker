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
              dockerImage = docker.build registry + ":$BUILD_NUMBER"//Biến môi trường tự sinh ra khi chạy pipeline
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

        stage('Deploy myweb With Docker') {
            steps {
//                sh 'docker stop myweb >/dev/null 2>&1'
//                sh 'docker rm myweb >/dev/null 2>&1'
                sh 'docker run --privileged --name myweb -d happyit/myweb:$BUILD_NUMBER'
            }
        }
    }



    }
}
