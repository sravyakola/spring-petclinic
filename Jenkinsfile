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

    stage('static analysis') {
      steps {
        sh '''./mvnw sonar:sonar \\
  -Dsonar.projectKey=Petclinic1 \\
  -Dsonar.projectName=\'Petclinic1\' \\
  -Dsonar.host.url=http://65.1.73.71:9000 \\
  -Dsonar.token=sqp_b9f52752f6fc0ad4e9877181587503546f8601a2'''
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

    stage('deploy') {
      parallel {
        stage('deploy') {
          steps {
            sh './mvnw spring-boot:run </dev/null &>/dev/null &'
          }
        }

        stage('Integration and performance tests') {
          steps {
            sh './mvnw verify'
            junit '**/target/surefire-reports'
          }
        }

      }
    }

  }
}