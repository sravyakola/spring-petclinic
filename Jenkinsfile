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

    stage('Static analysis') {
      steps {
        sh '''./mvnw sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.projectName=\'Petclinic\' \\
  -Dsonar.host.url=http://43.205.123.80:9000 \\
  -Dsonar.token=sqp_780ed06821e26980da2dc7e8e82019ba0293a3a3'''
      }
    }

  }
}