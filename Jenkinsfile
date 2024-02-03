pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''./mvnw sonar:sonar \\
  -Dsonar.projectKey=PetClinic \\
  -Dsonar.projectName=\'PetClinic\' \\
  -Dsonar.host.url=http://172.31.84.37:9000 \\
  -Dsonar.token=sqp_7263100c62bb6895ac3df3dcce79c52560a34b4a'''
      }
    }

    stage('Unit Test') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
      }
    }

  }
}