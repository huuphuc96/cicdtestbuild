pipeline {
    agent none

    stages {
       stage('Build') {
 steps {
  bat "dotnet build --configuration Release"
 }
}
 }
        

        
        post{
  always{
    emailext body: "${currentBuild.currentResult}: Job   ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
    recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
    subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
    }
  }
    
}
