
  pipeline {
    agent { label 'Test' }
    
    tools {
        maven 'maven3'
        jdk 'jdk17'
        // Ensure this tool is configured
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('Test') {
            steps {
               sh 'mvn tests'
            }
        }
        stage('Publish') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}

