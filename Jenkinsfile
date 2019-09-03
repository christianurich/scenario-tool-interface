pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker image build -t scenario-tool-interface .'
      }
    }
    stage('Testing') {
      steps {
        sh '''set +e
docker run --name sample -e USERNAME="test@unit.com" -e PASSWORD="rejudo01" -e USERNAME_GUEST="guest@unit.com" -e PASSWORD_GUEST="rejudo01" -e USERNAME_ADMIN="admin@danceplatform.org" -e PASSWORD_ADMIN="password"  scenario-tool-interface
set -e'''
        sh '''docker cp sample:/tmp/test.xml .
docker rm -f sample'''
      }
    }
  }
}