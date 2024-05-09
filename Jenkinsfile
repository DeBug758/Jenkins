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
                sh 'docker run -d --expose 3000 -p 3000:3000 nodedev:v1.0'
            }   
        }
        
    }
}
