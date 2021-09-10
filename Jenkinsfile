pipeline {
  agent {
    // this image provides everything needed to run Cypress
    docker {
      image 'cypress/base:14.17.0'
    }
  }

  stages {
    stage('build and test') {
      steps {
        sh "yarn install"
        sh "yarn update"
        sh "yarn run cy:attachments.spec"
      }
    }
  }
}
