pipeline {
    
    agent any
    
    tools {
        maven "Maven_mh"
    }
    
    stages {
        stage('git checkout') {
            steps{
            git branch: 'main', credentialsId: 'git_cred', url: 'https://github.com/mythreya23/WebExample_Maven.git'
            }
                
            }
        stage('Build') {
            steps{
            bat 'mvn clean install'
                 }
        }
        
        stage('Code quality') {
            steps{
            bat 'mvn sonar:sonar'
                 }
        }
        stage('deploy') {
            steps{
            deploy adapters: [tomcat8(credentialsId: 'Tomcat_cred', path: '', url: 'http://localhost:8085/')], contextPath: ' WebappPipeline', war: '**/*.war'
        }
        }
     
    }
    
        
    }





    
    
    
