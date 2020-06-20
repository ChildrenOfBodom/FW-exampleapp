pipeline {
  agent {
    node {
      label 'master'
    }
  }
  stages {
    stage('Build result') {
      steps {
        sh 'docker build -t dockersamples/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker build -t dockersamples/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build -t dockersamples/worker ./worker'
      }
    }
    stage('Docker-Compose') {
      steps {
        sh 'docker-compose -f docker-compose-simple.yml down'
        sh 'docker-compose -f docker-compose-simple.yml up -d'
      }
    }
    stage('Delete old images') {
      steps {
        sh 'docker images -q -f dangling=true | xargs -I ARGS docker rmi -f ARGS'
      }
    }
  }
}
