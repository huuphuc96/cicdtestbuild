
pipeline {
    agent any
    stages{
        stage ('Build') {
        steps{ 
            git url: 'https://github.com/cyrille-leclerc/multi-module-maven-project'
        }
        }
    
    
    stage ('Install Stage') {
    steps {
    bat'mvn install'

    }
    }
    }
    
    
}
