pipeline {
  agent {
    node {
      label 'master'
    }
  }
  stages {
    stage('Build result') {
      steps {
        sh 'docker rebuild -t dockersamples/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker rebuild -t dockersamples/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'docker rebuild -t dockersamples/worker ./worker'
      }
    }
    stage('Docker-Compose') {
      steps {
        sh 'docker-compose down'
        sh 'docker-compose -f docker-compose-simple.yml up -d'
      }
    }
  }
}
