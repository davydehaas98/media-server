pipeline {
  agent any
  options {
    disableCurrentBuilds()
    timeout(time: 10, unit: 'MINUTES')
  }
  stages {
    stage('Verify') {
      sh 'docker-compose --version'
      sh 'which docker-compose'
    }
    stage('Deploy') {
      sh 'docker-compose up -d --force-recreate'
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
