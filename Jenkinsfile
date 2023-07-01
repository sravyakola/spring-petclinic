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
  -Dsonar.token=sqp_4a6fa623c9e31a35d3e792ad2739e898ae58885'''
      }
    }

  }
}