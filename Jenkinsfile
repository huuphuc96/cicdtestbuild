pipeline { agent any stages { stage ('Compile Stage') {

        steps {
            withMaven(maven : 'apache-maven-3.6.1') {
                bat'mvn clean compile'
            }
        }
    }
} }
pipeline {
    agent any

stages {
    stage('Build') {
            steps {
                sh 'make' 
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
            }
        }
}
}
