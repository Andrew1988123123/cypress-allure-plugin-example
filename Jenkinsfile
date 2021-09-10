pipeline {
  agent {
    // this image provides everything needed to run Cypress
    any {
      image 'cypress/base:10'
    }
  }

  stages {
    stage('build and test') {
      steps {
        sh "npm run allure:clear"
        sh 'npm run cy:cucumber:run'
        sh "npm run allure:report"
      }
    }
  }
      post {
          always {
              script { // Wygenerowanie raportu allurowego
                  allure([
                          includeProperties: false,
                          jdk              : '',
                          properties       : [],
                          reportBuildPolicy: 'ALWAYS',
                          results          : [[path: 'target/allure-results']]
                  ])
              }
          }
      }
}
