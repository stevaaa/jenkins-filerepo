pipeline {
  agent any

  parameters {
    string(name: 'tomcat_dev', defaultValue: 'localhost:8080', description: 'Staging Server')
    string(name: 'tomcat_prod', defaultValue: 'localhost:8090', description: 'Production Server')
  }

  triggers {
    pollSCM('* * * * *')
  }

  stage ('Deployments') {
    parallel {
      stage('Deploy to Staging'){
        steps {
          sh 'mvn clean package'
        }
      }
      stage('Deploy to Production'){
        steps {
          sh 'mvn clean package'
        }
      }
    }
  }
}
