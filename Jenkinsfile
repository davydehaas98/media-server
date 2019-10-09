pipeline {
  agent any
  options {
    disableConcurrentBuilds()
    timeout(time: 10, unit: 'MINUTES')
  }
  stages {
    stage('Verify') {
      steps {
        sh 'docker-compose --version'
        sh 'which docker-compose'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker-compose -p media-server up -d --force-recreate'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
