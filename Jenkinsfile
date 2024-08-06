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
                sh 'm clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    emailext attachLog: true, body: 'Congragulation your build success', subject: 'Success', to: 'satishkumarpanda99@gmail.com'
                }
          failure {
                    emailext body: 'Congragulation your build failure', subject: 'Failure', to: 'satishkumarpanda99@gmail.com'
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
