pipeline {
  agent {
    node {
      label 'test'
    }

  }
  stages {
    stage('Complie') {
      steps {
        sh './mvnw clean compile'
      }
    }

  }
}