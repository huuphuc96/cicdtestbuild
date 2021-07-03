
pipeline {
    agent any
    
    stage ('Build') {
        steps{ 
            git url: 'https://github.com/cyrille-leclerc/multi-module-maven-project'
        }
        steps{
            withMaven {
      sh "mvn clean verify"
    } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
        }
    
    
    stage ('Install Stage') {
    steps {
    bat'mvn install'

    }
    }
    
}
}
