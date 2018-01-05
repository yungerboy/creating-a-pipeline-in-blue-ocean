def  version

pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'node:9.3.0-alpine'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Delivery') {
      agent any
      steps {
        sh './jenkins/scripts/deliver.sh'
		script {
		   version = input(message: 'Please check whether OK', submitterParameter: 'VERSION')
		}
     
        sh './jenkins/scripts/kill.sh'
		echo "This is User Input Version $version "
      }
    }
  }
}