pipeline {
  agent {
     dockerfile {
        filename 'Dockerfile.build'
        lebel 'build'
       // args '-v'
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
  
