pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: 'http://localhost', description: 'Staging Server')
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
                archiveArtifacts '**/*.war'
            }
        }
    }

    stage ('Deploy to Staging'){
        steps {
            sh "cp -f **/target/*.war tomcat@${params.tomcat_dev}:8090/webapps"

        }
    }     
    }
}
