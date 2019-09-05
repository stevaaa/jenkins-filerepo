pipeline{
  agent any
  tools {
    maven 'localMaven'
    jdk 'localJDK'
  }
  
  parameters{
    string(name: 'tomcat_dev', defaultValue: 'localhost:8080', description: 'Staging Server')
    string(name: 'tomcat_prod', defaultValue: 'localhost:8090', description: 'Production Server')
  }

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Build'){
      steps {
        sh 'mvn clean package'
      }
      post {
        success {
          echo 'Now archiving'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
   stage('Deployments') {
      parallel {
        stage('Deploy to Staging'){
          steps {
            sh 'echo ${params.tomcat_dev}'
          }
        }
        stage('Deploy to Production'){
          steps {
            sh 'echo ${params.tomcat_prod}'
          }
        }
      }
    }
  }
}
