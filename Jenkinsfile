pipeline {
  agent {
    node {
      label 'master'
    }
  }
  stages {
    stage('Re/Build result') {
      steps {
        script {
        sh 'docker build -t dockersamples/result ./result'
        }
      }
    } 
    stage('Re/Build vote') {
      steps {
        script {
        sh 'docker build -t dockersamples/vote ./vote'
        }
      }
    } 
    stage('Re/Build worker') {
      steps {
        sh 'docker build -t dockersamples/worker ./worker'
      }
    }
    stage('Docker-Compose') {
      steps {
        sh 'docker-compose down'
        sh 'docker-compose up -d --force-recreate'
      }
    }
    stage('Delete old images') {
      steps {
        sh 'docker images -q -f dangling=true | xargs -I ARGS docker rmi -f ARGS'
      }
    }
  }
}
