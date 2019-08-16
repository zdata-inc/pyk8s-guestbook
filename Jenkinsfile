pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        git(url: 'https://github.com/zdata-inc/pyk8s-guestbook/tree/master/flask-redis', branch: 'master')
      }
    }
  }
}