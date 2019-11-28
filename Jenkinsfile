#!groovy
pipeline {
    agent{
        docker {
            image 'python:3.7.1'
        }
    }
    stages {
        stage('Build') {
           steps{
            sh 'git checkout'
            sh 'python -m venv ../.env'
            sh 'source ../.env/bin/activate'
            sh 'pip install -r '
           }
       }
       stage('App Tests') {
           steps {
               sh 'pytest --junitxml test-reports/app-tests.xml ./'
           }
           post {
               always {
                   junit 'test-reports/results.xml'
               }
           }
       }
       stage('Lint Tests') {
           steps {
               sh 'flake8 -output-file flake8.txt'
           }
           post {
               always {
                   sh 'flake8_junit flake8.txt test-reports/lint-tests.xml'
                   junit 'test-reports/lint-tests.xml'
               }
           }
       }
    }
}
