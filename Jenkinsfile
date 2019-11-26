#!groovy

pipeline {
  agent { docker { image 'node:10.16.0-alpine' } }
  stages {
    stage('checkout') {
      steps {
        checkout scm
        sh 'echo $BRANCH_NAME'
      }
    }
    //stage('Clone Repository') {
      //checkout scm
    //}

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Tests') {
      steps {
        sh 'npm test'
      }
    }
  }
}
