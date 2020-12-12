pipeline {
  agent {
     docker {
       image 'lebedevds/build-war'
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

      }
    }
  }
}
  
