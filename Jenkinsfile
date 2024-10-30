pipeline {
    agent { label 'Test' }
    
    tools {
        maven 'maven3' 
        jdk 'jdk17'// Ensure this tool is correctly configured in Jenkins
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {  // Use 'steps' instead of 'step'
                echo 'Running tests...'
            }
        }
        stage('Publish') {  // Fixed the spelling from 'punlish' to 'Publish'
            steps {  // Use 'steps' for consistency
       
