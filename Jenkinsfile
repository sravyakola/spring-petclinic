pipeline {
  agent any
  stages {
    stage('Complie') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('static analysis') {
      steps {
        sh '''./mvnw sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.projectName=\'Petclinic\' \\
  -Dsonar.host.url=http://localhost:9000 \\
  -Dsonar.token=sqp_aad6bfd0a18c572ffb202780c7d2a0e853d3b755'''
      }
    }

    stage('Unit test') {
      steps {
        sh '''./mvnw "-Dtest=**/petclinic/*/*.java" test
'''
      }
    }

    stage('Package') {
      steps {
        sh '''./mvnw package -DskipTests=true
'''
      }
    }

  }
}