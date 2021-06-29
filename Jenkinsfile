pipeline {

  agent none

  environment {
    DOCKER_IMAGE = "huuphucitc/flask-docker"
  }

  stages {
    

    stage("build") {
      agent { node {label 'master'}}
      environment {
        DOCKER_TAG="${GIT_BRANCH.tokenize('/').pop()}-${GIT_COMMIT.substring(0,7)}"
      }
      steps {
        
      dockerImage = docker.build("username/repository:tag")
      docker.withRegistry('https://registry-1.docker.io/v2/', 'docker-hub-credentials') {
        dockerImage.push()
      }
        

        //clean to save disk
        sh "docker image rm ${DOCKER_IMAGE}:${DOCKER_TAG}"
        sh "docker image rm ${DOCKER_IMAGE}:latest"
      }
    }
  }

  post {
    success {
      echo "SUCCESSFUL"
    }
    failure {
      echo "FAILED"
    }
  }
}
