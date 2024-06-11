@Library('shared-library') _

pipeline {
    agent any

    environment {
        TERRAFORM_DIR = 'terraform'
    }

    stages {
        stage('run terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    terraform() {
                        terraformInit()
                        terraformPlan()
                        terraformApply()
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
