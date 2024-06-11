pipeline {
    agent any

  environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID') // Credentials ID for access key
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY') // Credentials ID for secret access key
        AWS_REGION            = 'us-east-1'
    }
    stages {
        stage('Initialize Terraform') {
            steps {
             
                    script {
                        // Initializes Terraform, downloads necessary plugins, etc.
                        sh 'terraform init'
                    }
                }
           }
        stage('Plan Terraform') {
            steps {
                    script {
                        // Generates an execution plan for Terraform
                        sh 'terraform plan -out=plan.tfplan'
                    }
                }
           }
        stage('Apply Terraform') {
            steps {
                        sh 'terraform apply "plan.tfplan"'
                    }
                }
            }     
    post {
        always {
            // Clean up workspace after pipeline execution
            cleanWs()
        }
    }
}
