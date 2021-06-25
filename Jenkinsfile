pipeline {
    agent any
    environment {
      DOCKER_TAG = getVersion()
    }
        stage('Stage Build With Docker image') {
            steps {         
                sh 'docker build . -t happyit/myapp:${DOCKER_TAG}'
            }
        }

        stage('Stage Docker Hub Push') {
            steps { 
                withCredentials([string(credentialsId: 'docker_hub', variable: 'DockerHubPwd')]) {
                    sh 'docker login -u happyit -p ${DockerHubPwd}'
                }               
                sh 'docker push happyit/myapp:${DOCKER_TAG}'
            }
        }

        stage('Deploy my app Docker') {
            steps {                         
                sh 'docker push happyit/myapp:${DOCKER_TAG}'
            }
        }
                    
    }
}

def getVersion(){
    def commitHash = sh label: '', returnStdout: true, script: 'git rev-parse --short HEAD'
    return commitHash
}