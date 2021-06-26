pipeline {
    agent any
    environment {
      DOCKER_TAG = getVersion()
      registry = "happyit/myweb"
    }

    stages {

        
        stage('Build image code version 2') {
          steps{
            script {
              dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
          }
        }       

//        stage('Stage Build With Docker image') {
//            steps {
//                sh 'docker build . -t happyit/myweb:${DOCKER_TAG}'
//            }
//        }

        stage('Stage Docker Hub Push') {
            steps { 
                withCredentials([string(credentialsId: 'docker_hub', variable: 'DockerHubPwd')]) {
                    sh 'docker login -u happyit -p ${DockerHubPwd}'
                }          
                sh "docker push happyit/myweb:${DOCKER_TAG}"
            }
        }

        stage('Deploy myweb With Docker') {
            steps {
//                sh 'docker stop myweb >/dev/null 2>&1'
//                sh 'docker rm myweb >/dev/null 2>&1'
                sh 'docker run --privileged --name myweb -d happyit/myweb:${DOCKER_TAG}'
            }
        }
    }
}

def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}