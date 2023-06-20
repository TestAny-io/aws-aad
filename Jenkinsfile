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
    stage('Environments') {
      steps {
        sh 'cat /etc/os-release'
        sh 'uname -a'
        sh 'env'
        sh 'pwd'
        sh 'ls -lah'
      }
    }
    stage('Fetch dependencies') {
      steps {
        sh 'go mod download'
      }
    }
    stage('Unit Test') {
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