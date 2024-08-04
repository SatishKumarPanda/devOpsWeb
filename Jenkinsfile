pipeline {
    agent any
    
    tools {
        maven 'local maven'
    }
    triggers {
         pollSCM('* * * * *')
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
                emailext attachLog: true, body: 'Build now created', subject: 'Success build', to: 'satishpanda430@gmail.com'
                }
        
            }
            }
              stage('Deployment'){
            steps {
                echo 'Sucessfully Deploy'
            }
        }
        
    
            }
}
