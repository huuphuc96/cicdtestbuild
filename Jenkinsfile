pipeline {
    agent none

    stages {
        stage('Build'){
   steps{
      bat "dotnet build C:\Website\\Projectvip.csproj --configuration Release"
    }
 }
        stage('Publish'){
     steps{
       bat "dotnet publish C:\Website\\Projectvip.csproj "
     }
}
        stage('Deploy') {
            steps {
                echo 'Deploying....'
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
}
