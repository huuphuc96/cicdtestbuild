
pipeline {
    agent any
    stage{
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
