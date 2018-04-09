pipeline {
    agent any

parameters {
         string(name: 'tomcat_dev', defaultValue: 'localhost', description: 'Staging Server')
}   
 
    tools {
        maven 'localMAVEN'
    }
 
stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
        }

        stage ('Deploy to Staging'){
                steps {
                sh "cp -i **/target/*.war ${params.tomcat_dev}:/Users/danny/Documents/apache-tomcat-8.5.29/webapps"
            }
        }
        post {
            success {
                echo 'Now Archiving...'
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
                    
    }
}
