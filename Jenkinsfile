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
        sh '''mvn clean verify sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.projectName=\'Petclinic\' \\
  -Dsonar.host.url=http://172.31.27.16:9000 \\
  -Dsonar.token=sqp_03be67247586069cc631310922f9f8d093ca4333'''
      }
    }

  }
}