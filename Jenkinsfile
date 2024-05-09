pipeline {
    
    agent any
    tools {
        nodejs "node"   
    }
    
    stages {
        
        stage("build") {
            
            steps{
                sh 'npm install'
            }
            
        }

        stage("test") {
            
            steps{
                sh 'npm test'
            }   
        }

        stage("Docker build") {
            
            steps{
                sh 'docker build -t nodemain:v1.0 .'
            }   
        }

        stage("deploy") {
            
            steps{
                sh 'docker remove -f $(docker ps -q  --filter ancestor=nodemain:v1.0)'
                sh 'docker run -d --expose 3000 -p 3000:3000 nodemain:v1.0'
            }   
        }
        
    }
}
