pipeline {
    agent any
tools {
    maven 'local maven'
stages{
        stage('Build'){
            steps {
                sh "mvn clean build"
            }
        }
             stage('deploy'){
            steps {
                echo "mvn clean package"
            }
         }
}
        
    }
}
