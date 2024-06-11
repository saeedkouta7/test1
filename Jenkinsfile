pipeline {
    agent any


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
