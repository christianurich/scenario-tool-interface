pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker image build -t scenario-tool-interface .'
      }
    }
  }
}