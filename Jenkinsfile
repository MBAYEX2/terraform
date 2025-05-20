pipeline {
    agent any

    environment {
        TERRAFORM_DIR = 'Terraform_Fil_Rouge'
    }

    stages {
        stage('Checkout du code') {
            steps {
                git branch: 'main', url: 'https://github.com/MBAYEX2/terraform.git'
            }
        }

        stage('Initialisation de Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'sudo terraform init'
                }
            }
        }

        stage('Plan Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'sudo terraform plan'
                }
            }
        }

        stage('Application de Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'sudo terraform apply -auto-approve'
                }
            }
        }
    }
}
