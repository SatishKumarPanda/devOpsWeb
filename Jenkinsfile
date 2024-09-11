pipeline {
    agent any
    
    tools {
        maven 'maven'
    }
	 environment {     
         DOCKERHUB_CREDENTIALS= credentials('docker-hub')     
       } 

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package -Dmaven.test.skip=true'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    stage('Build Docker Image') {         
      steps{                
	sh 'docker build -t satishkumarpanda/devopsweb:$BUILD_NUMBER .'           
        echo 'Build Image Completed'                
      }           
    }   
   stage('Login to Docker Hub') {         
      steps{                            
	sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'                 
	echo 'Login Completed'                
      }           
    }
 stage('Push Image to Docker Hub') {         
      steps{                            
	sh 'docker pushj satishkumarpanda/devopsweb:$BUILD_NUMBER'                 
  echo 'Push Image Completed'       
      }           
    }
    }
}
