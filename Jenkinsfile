pipeline {
    
    agent any
    tools {nodejs "node"}
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
               sh 'docker build -t nodedev:v1.0 .'
            }   
        }

        stage("deploy") {
            
            steps{
                sh 'docker remove -f $(docker ps -q  --filter ancestor=nodedev:v1.0)'
                sh 'docker run -d --expose 3001 -p 3001:3000 nodedev:v1.0'
            }   
        }
        
    }
}
