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

    stage('Unit Test') {
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

    stage('Deploy') {
      steps {
        sh './mvnw spring-boot:run </dev/null &>/dev/null &'
      }
    }

  }
}