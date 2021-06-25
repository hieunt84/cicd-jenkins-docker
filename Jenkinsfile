pipeline {
    agent any
    environment {
      DOCKER_TAG = getVersion()
    }

    stages {
        stage('Stage Build With Docker image') {
            steps {
                sh 'docker build . -t happyit/myweb:${DOCKER_TAG}'
            }
        }

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
                sh 'docker run --privileged -p 80:80 --name myapp -d happyit/myweb:${DOCKER_TAG}'
            }
        }
    }
}

def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}