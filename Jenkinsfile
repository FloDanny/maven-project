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
            sh "cp **/*.war ~.../Users/danny/Documents/apache-tomcat-8.5.29/"
        }
    }     
    }
}
