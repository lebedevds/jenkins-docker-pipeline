pipeline {
  agent {
     docker {
       image 'lebedevds/build-war'
       args '-u root --privileged -v /var/run/docker.sock:/var/run/docker.sock'
       }
  }
  stages {
    stage ('Build war file') {
      steps {
        git 'https://github.com/lebedevds/test-webapp.git'
        sh 'mvn package'
      }
    }
   stage ('Building image') {
      steps {
       sh 'docker build . --tag=$NAME'
       sh 'docker login -u lebedevds -p $password'
       sh 'docker tag $NAME $NAME && docker push $NAME'
        }
      }
    stage('Run docker on prod') {
      steps {
        sh 'ssh-keyscan -H jenkins >> ~/.ssh/known_hosts'
        sh 'ssh@$prod_ip docker pull $NAME'
        sh 'ssh@$prod_ip docker run -d -p 8080:8080 $NAME'
      }
    }
  }
}
