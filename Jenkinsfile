pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        git(url: 'https://github.com/zdata-inc/pyk8s-guestbook.git', branch: 'master')
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
}
