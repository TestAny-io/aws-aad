pipeline {
  agent any

  stages {
    stage('Unit Test') {
      steps {
        echo 'Unit Testing..'
        checkout scm
        sh 'make test'
      }
    }
    stage('Build') {
      steps {
        echo 'Building..'
        checkout scm
        sh 'make all'
        archiveArtifacts artifacts: '**/dist/*', fingerprint: true
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
        echo 'Skip testing because we are not there yet'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        echo 'Skip deployment because we are not there yet'
      }
    }
  }
}