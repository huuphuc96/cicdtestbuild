pipeline {
    agent any

stages {
    stage('Build') {
            steps {
                sh 'make' 
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
            }
        }
    stage('Deploy'){
"C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:iisApp="${WORKSPACE}\\${"projectvip"}" -enableRule:AppOffline -dest:iisApp="${iisApplicationName}",ComputerName="https://103.77.166.18:1995/msdeploy.axd",UserName="$USERNAME",Password="$PASSWORD",AuthType="Basic" -allowUntrusted"""}
    }
}
}
