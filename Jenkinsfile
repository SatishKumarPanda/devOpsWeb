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
	sh 'docker push satishkumarpanda/devopsweb:$BUILD_NUMBER'                 
  echo 'Push Image Completed'       
      }           
    }
	 stage('Run Container on Dev Server') {         
    steps{
	       script {
      def dockerRun = "docker run -p 8282:8080 -d --name myweb satishkumarpanda/devopsweb:$BUILD_NUMBER"
  
	    sshagent(['webserver']){
      //sh "ssh -o StrictHostKeyChecking=no ec2-user@3.110.134.52 ${dockerdel}"
       sh "ssh -o StrictHostKeyChecking=no ec2-user@65.0.89.79 ${dockerRun}"
}
	       }
    }       
    } 
    }
}
