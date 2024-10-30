pipeline {
    agent { label 'Test' }
    
    tools {
        maven 'local maven'  // Ensure this tool is correctly configured in Jenkins
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
       
