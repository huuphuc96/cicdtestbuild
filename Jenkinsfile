
pipeline {
    agent any

stages {
        stage ('Compile Stage') {
steps {
bat'mvn clean compile'

}
}
stage ('Testing Stage') {
steps {
bat'mvn test'

}
}
    stage ('Ste') {
        steps{ 
            git url: 'https://github.com/cyrille-leclerc/multi-module-maven-project'
        }
        steps{
            withMaven {
      sh "mvn clean verify"
    } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
        }
    
  }
    
stage ('Install Stage') {
steps {
bat'mvn install'

}
}
    stage('Build') {
            steps {
                sh 'make' 
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
            }
        }
}
}
