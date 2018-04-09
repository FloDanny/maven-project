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

    stage ('Deploy to Staging'){
        steps {
            build 'deploy-to-staging'
        }
      }     
    }
}
