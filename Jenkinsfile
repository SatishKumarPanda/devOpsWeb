pipeline {
    agent any
    
    tools {
        maven 'local maven'
    }

    stages {
        stage ('build application'){
        step {
            echo 'mvn clean package'
        }
            post {
             success {
                 echo "archiving artifact"
                 archiveArtifacts artifacts: '**/target/*.war'
             }
            }
       }
         stage ("deploy server"){
             parallel {
                  stage ('deploy 1'){
        step {
            deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://3.110.29.156:8080')], contextPath: null, war: '**/*.war'
        }
             }
                  stage ('deploy 2'){
        step {
            echo "Deploying tomcat server"
        }
         }
    }
         }
    }
}
