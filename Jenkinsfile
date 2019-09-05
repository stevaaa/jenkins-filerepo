pipeline {
  agent any
  stages {
    stage('Build'){
      steps {
        sh 'export PATH="/Users/stephensam/projects/apache-maven-3.6.1/bin:$PATH"'
        sh 'mvn --version'
        sh 'mvn clean package'
      }
      post {
        success {
          echo 'Now archiving'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
  }
}
