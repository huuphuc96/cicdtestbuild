
pipeline {
    agent any
    stages{
        stage ('Build') {
        steps{ 
            git url: 'https://github.com/cyrille-leclerc/multi-module-maven-project'
        }
        }
    
        stage('Publish'){
     steps{
         
         bat "dotnet publish ../../src/projectvip/projectvip.csproj --configuration Release --no-restore"
     }
}
        
    }
    
    
}
