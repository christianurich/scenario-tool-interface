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
docker run --name $UNIQUE_ID -e USERNAME="test@unit.com" -e PASSWORD=$PASSWORD -e USERNAME_GUEST="guest@unit.com" -e PASSWORD_GUEST=$PASSWORD_GUEST -e USERNAME_ADMIN="admin@danceplatform.org" -e PASSWORD_ADMIN=$PASSWORD_ADMIN  scenario-tool-interface
set -e'''
        sh '''docker cp sample:/tmp/test.xml .
docker rm -f $UNIQUE_ID'''
        junit 'test.xml'
      }
    }
  }
  environment {
    PASSWORD = credentials('test@unit.com')
    PASSWORD_GUEST = credentials('guest@unit.com')
    PASSWORD_ADMIN = credentials('admin@danceplatform.org')
    UNIQUE_ID = UUID.randomUUID().toString()
  }
}