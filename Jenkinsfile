pipeline {
    agent any

    //Kaynak kodun adresi
String githubUrl = "https://github.com/huuphuc96/cicdtestbuild"

//Kaynak kodun içerisindeki projenin ismi
String projectName = "cicdtestbuild/projectvip"

//Kaynak kodun publish edileceği dizin
String publishedPath = "cicdtestbuild\\projectvip\\bin\\Release\\netcoreapp2.2\\publish"

//Hedef makinesindeki IIS'de tanımlı olan sitenizin ismi
String iisApplicationName = "projectvip"

//Hedef makinesindeki IIS'de tanımlı olan sitenizin dizini
String iisApplicationPath = "C:\\Website\\PhucDepTrai_LandingPAGE"

//Hedef makinesinin IP'si
String targetServerIP = "0.0.0.0"

node () {
    stage('Checkout') {
        checkout([
            $class: 'GitSCM', 
            branches: [[name: 'master']], 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [], 
            submoduleCfg: [], 
            userRemoteConfigs: [[url: """ "${githubUrl}" """]]])
    }
    stage('Build') {
        bat """
        cd ${projectName}
        dotnet build -c Release /p:Version=${BUILD_NUMBER}
        dotnet publish -c Release --no-build
        """
    }
    stage('Deploy'){
      bat """ "C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:iisApp="${WORKSPACE}\\${publishedPath}" -enableRule:AppOffline -dest:iisApp="${iisApplicationName}",ComputerName="https://${targetServerIP}:8172/msdeploy.axd",UserName="$USERNAME",Password="$PASSWORD",AuthType="Basic" -allowUntrusted"""}
    }

}
