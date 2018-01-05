pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'node:6.12.3-alpine'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
  }
}