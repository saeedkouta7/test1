@Library('shared-library') _

pipeline {
    agent any
    

    stages {
         stage('run terraform') {
            dir("terraform"){ 
              steps {
                  script {
                      terraform()
                }
            }
        }
     }          
 } 
    post {
        always {
            cleanWs()
        }
    }
}
