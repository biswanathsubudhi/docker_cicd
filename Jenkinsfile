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
          sh "docker login -u biswanathsubudhi -p ${dockerpassword}"
          sh "docker push biswanathsubudhi/myapp"
        }
      }
    }
    stage('push the doce to docker-dev server for deployment') {
      steps {
        sshagent(['docker_dev']) {
        sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.37.5 docker container rm -f application "
        sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.37.5 docker run -itd -p 8080:8080 --name application biswanathsubudhi/myapp"
        }
      }
    }
  }
}  
