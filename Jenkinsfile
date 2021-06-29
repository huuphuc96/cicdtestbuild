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
      stage('Build image') {
			steps {
				sh 'docker build -t {IMAGE_NAME} .'
			}
		} 

        stage('Push image') {
			steps {
				script {
					docker.withRegistry('https://{ACCOUNT_ID}.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:aws-credentials') {
						docker.image('{IMAGE_NAME}').push("v${env.BUILD_NUMBER}")
						docker.image('{IMAGE_NAME}').push('latest')
					}
				}
			}
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
