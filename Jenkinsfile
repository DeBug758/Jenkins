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
                docker build -t nodemain:v1.0 .
            }   
        }

        stage("deploy") {
            
            steps{
                docker run -d --expose 3000 -p 3000:3000 nodemain:v1.0
            }   
        }
        
    }
}
