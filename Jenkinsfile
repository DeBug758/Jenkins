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
                sh 'docker run -d -p 3000:3001 nodedev:v1.0'
            }   
        }
        
    }
}
