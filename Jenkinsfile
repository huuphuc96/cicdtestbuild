
pipeline {
    agent any
    
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
