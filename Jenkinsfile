pipeline {
  agent any
  stages{
    stage('Build'){
      steps{
        sh 'mvn clean package'
        sh 'docket build . -t tomcatwebapp:${env.BUILD_ID}'
      }
    }
  }
}
