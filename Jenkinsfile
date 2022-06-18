pipeline {
  agent any
  stages {
    stage('Code for Build using Maven') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Code for Dcoker BUild') {
      steps {
        echo ("Code for Dcoker BUild")
      }
    }
    stage('Code for pushing the docker image to docker hub') {
      steps {
        echo ("Code for pushing the docker image to docker hub")
      }
    }
    stage('push the doce to docker-dev server for deployment') {
      steps {
        echo ("push the doce to docker-dev server for deployment")
      }
    }
  }
}  
