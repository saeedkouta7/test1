pipeline {
    agent any

    environment {
        TERRAFORM_DIR = '/home/saeed/ivolve-grad-project/terraform'
  // Adjust this path to where your Terraform files are located
        // You can set environment variables here to configure Terraform or use secrets from Jenkins credentials
    }

    stages {
        stage('Initialize Terraform') {
            steps {
                dir(env.TERRAFORM_DIR) {
                    script {
                        // Initializes Terraform, downloads necessary plugins, etc.
                        sh 'terraform init'
                    }
                }
            }
        }
        stage('Plan Terraform') {
            steps {
                dir(env.TERRAFORM_DIR) {
                    script {
                        // Generates an execution plan for Terraform
                        sh 'terraform plan -out=plan.tfplan'
                    }
                }
            }
        }
        stage('Apply Terraform') {
            steps {
                dir(env.TERRAFORM_DIR) {
                    script {
                        // Applies the changes required to reach the desired state of the configuration
                        sh 'terraform apply "plan.tfplan"'
                    }
                }
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
