
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
       bat "dotnet publish C:\\Website\\PhucDepTrai_LandingPAGE"
     }
}
        
    }
    
    
}
