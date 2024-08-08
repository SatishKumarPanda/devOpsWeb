pipeline {
    agent any
    
    tools {
        maven 'local maven'
    }
    envitonment {
        AWS_ACCESS_KEY_ID    = credentials('jenkins-aws-secret-key-id')
        AWS-SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

stages{
        stage('Build'){
            steps {
                echo 'build'
            }
        }
            stage('Test'){
                step{ 
                    echo 'test'
            }
            }
                stage('punlish'){
                    step {
                        sh 'mvn clean package'
                    }
            post {
                success {
                    sh 'aws configure set region ap-south-1'
                    sh 'aws s3 cp ./workspace/*.war s3:jenkinsstorebucket1
                }
            }
            }
        
    
            }
}
