pipeline {
    agent any
    
    tools {
        maven 'local maven'
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
        }
                stage ("Deploy to Staging"){
                    steps {
                        sh "scp **/*.war root@13.233.138.96:/opt/tomcat/webapps/"
                    }
                }
            }
        }
