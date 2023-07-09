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
  -Dsonar.projectKey=Petclinic1 \\
  -Dsonar.projectName=\'Petclinic1\' \\
  -Dsonar.host.url=http://65.2.54.120:9000 \\
  -Dsonar.token=sqp_b3d723bc8c2df1176cfa7d1129027a77cb3f85c9'''
      }
    }

  }
}