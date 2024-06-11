@Library('shared_library') _

pipeline {
    agent any

    environment {
        TERRAFORM_DIR = 'terraform'
    }

    stages {
        stage('Terraform Init') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    script {
                        terraformInit()
                    }
                }
            }
        }
        stage('Terraform Plan') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    script {
                        terraformPlan('tfplan')
                    }
                }
            }
        }
        stage('Terraform Apply') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    script {
                        terraformApply('tfplan')
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
