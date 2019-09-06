pipeline {
  agent any
  stages{
    stage('Build'){
      steps{
        bat 'mvn clean package'
        bat 'docket build . -t tomcatwebapp:${env.BUILD_ID}'
      }
    }
  }
}
