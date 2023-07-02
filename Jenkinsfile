pipeline {
  agent {
    node {
      label 'test'
    }

  }
  stages {
    stage('compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

  }
}