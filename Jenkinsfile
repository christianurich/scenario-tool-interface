pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''docker rm -f sample
docker image build -t scenario-tool-interface .'''
      }
    }
  }
}