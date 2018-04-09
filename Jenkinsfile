pipeline {
    agent any
 
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
                archiveArtifacts '**/*.war'
            }
        }
    }

    stage ('Deployments'){
        parallel{
            stage ('Deploy to Staging'){
                steps {
                    build 'DeployToStaging'
                }
            } 
            stage ('Checkstyle Test'){
                steps {
                    build 'CheckstyleMaven'
                }
            }
        }
      }     
    }
}
