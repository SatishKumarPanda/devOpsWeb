pipeline {
    agent any
    
    tools {
        maven 'local maven'
    }
    triggers {
         pollSCM('* * * * *')
     }
    envitonment {
        AWS_ACCESS_KEY_ID    = credentials('jenkins-aws-secret-key-id')
        AWS-SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    sh 'aws configure set region ap-south-1'
                    sh 'aws s3 cp **/target/*.war s3://jenkinsstorebucket1
                }
            }
            }
        
    
            }
}
