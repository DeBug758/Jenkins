pipeline {
    
    agent any
    
    stages {
        
        stage("build") {
            
            steps{
                npm install
            }     
        }

        stage("test") {
            
            steps{
                npm test
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
