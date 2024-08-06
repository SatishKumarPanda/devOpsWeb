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
                    emailext body: 'Congragulation your build sucess', subject: 'Success', to: 'satishkumarpanda99@gmail.com'
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
