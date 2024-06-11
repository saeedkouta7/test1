@Library('shared-library') _

pipeline {
    agent any
    

    stages {
         stage('run terraform') {
             steps {
               dir("terraform"){ 
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
