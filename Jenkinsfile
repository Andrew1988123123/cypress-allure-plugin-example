pipeline {
agent any {
        docker {
            image 'cypress/base:12.16.1'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                git url: 'https://github.com/AndrzejSierocinski/cypress-allure-plugin-example.git'
                bat 'npm ci'
                bat 'npm run cy:verify'
            }
        }
        stage('Test') {
            steps {
                bat 'npm run cy:attachments.spec'
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
