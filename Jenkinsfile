pipeline {
    agent { label 'Test' }
    
    tools {
        maven 'local maven'
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
            }
        
    
            }
}
