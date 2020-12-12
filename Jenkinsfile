pipeline {
  agent {
     docker {
       image 'lebedevds/build-war'
       args '-v /var/run/docker.sock:/var/run/docker.sock'
       }
  }
  stages {
    stage ('Build war file') {
      steps {
      git 'https://github.com/lebedevds/test-webapp.git'
      sh 'mvn package'
      }
    }
    stage ('Build docker image') {
      steps {
      sh 'docker build https://github.com/lebedevds/jenkins-docker-pipeline.git -f Dockerfile.deploy'

      }
    }
  }
}
