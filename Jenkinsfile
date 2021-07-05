
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
         bat 'dotnet publish "projectvip/projectvip.csproj" -o "C:/Website/PhucDepTrai_LandingPAGE" '
     }
}
        
    }
    
    
}
