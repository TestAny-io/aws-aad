pipeline {
  agent any

  tools { go '1.19' }

  options {
    office365ConnectorWebhooks([[
      startNotification: true,
      notifySuccess: true,
      notifyAborted: false,
      notifyNotBuilt: false,
      notifyUnstable: false,
      notifyFailure: true,
      notifyBackToNormal: false,
      notifyRepeatedFailure: true,
      statusChangeOnly: true
    ]])
  }

  stages {
    staget('Environments') {
      description 'fetch environments information'
      steps {
        sh 'cat /etc/os-release'
        sh 'uname -a'
        sh 'env'
        sh 'pwd'
        sh 'ls -lah'
      }
    }
    stage('Fetch dependencies') {
      description 'download dependencies for the project'
      steps {
        sh 'go mod download'
      }
    }
    stage('Unit Test') {
      description 'complete unit test for existing branch'
      steps {
        sh 'make test'
      }
    }
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'make all'
        archiveArtifacts artifacts: '**/dist/*'
        fingerprint: true
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