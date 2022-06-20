pipeline {
  agent any
  tools {
    maven 'Maven3'
  }
  stages {
    stage('Code for Build using Maven') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Code for Dcoker BUild') {
      steps {
        sh "docker build . -t biswanathsubudhi/myapp"
      }
    }
    stage('Code for pushing the docker image to docker hub') {
      steps {
        withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerpassword')]) {
        // some block
        }
      }
    }
    stage('push the doce to docker-dev server for deployment') {
      steps {
        echo ("push the doce to docker-dev server for deployment")
      }
    }
  }
}  
