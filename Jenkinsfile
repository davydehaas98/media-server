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
            when {
                branch 'master'   
            }
            steps {
                hs 'docker-compose down -v -f'
                sh 'docker-compose -p media-server up -d'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
