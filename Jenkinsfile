pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: 'http://localhost:8090', description: 'Staging Server')
    }
 
    tools {
        maven 'localMAVEN'
    }
 
stages{
    stage('Build'){
        steps {
            sh 'mvn clean package'
            }
        post {
            success {
                echo 'Now Archiving...'
                archiveArtifacts '**/target/*.war'
            }
        }
    }

    stage ('Deploy to Staging'){
        steps {
            build 'deploy-to-staging'
        }
      }     
    }
}
