pipeline {
  agent any
  environment {
    // Keep both; one of them will be where Docker lives on macOS
    PATH = "/opt/homebrew/bin:/usr/local/bin:${env.PATH}"
  }
  stages {
    stage('Verify Docker') {
      steps {
        sh '''
          echo "whoami: $(whoami)"
          which docker || true
          docker version
        '''
      }
    }
    stage('Use Docker Image') {
      steps {
        script {
          docker.image('python:3.13.7-alpine3.22').inside {
            sh 'python --version'
          }
        }
      }
    }
  }
}
