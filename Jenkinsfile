pipeline {
    agent any
    tools {nodejs "node"}
    stages {
        stage('Node') {
            steps {
                git url: 'https://github.com/AndrzejSierocinski/cypress-allure-plugin-example.git'
                bat 'npm install'
                bat 'npm update'
                bat 'npm run allure:clear'
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
