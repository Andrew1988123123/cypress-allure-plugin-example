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
        sh "yarn install --unsafe-perm=true --allow-root cypress"
        sh "yarn update --unsafe-perm=true --allow-root cypress"
        sh "yarn run cy:attachments.spec"
      }
    }
  }
}
