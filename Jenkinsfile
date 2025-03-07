pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("your-dockerhub-username/hello-world:latest")
        }
      }
    }
    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PWD')]) {
          sh "docker login -u $DOCKER_USER -p $DOCKER_PWD"
          dockerImage.push()
        }
      }
    }
  }
}
