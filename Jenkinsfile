pipeline {
    agent any

    environment {
        PATH = "C:\\Users\\hp\\Desktop\\terraform_1.11.4_windows_amd64;${env.PATH}"
        TERRAFORM_DIR = 'Terraform_Fil_Rouge'
    }

    stages {
        stage('Checkout du code') {
            steps {
                git branch: 'main', url: 'https://github.com/fatou0409/terraform_fil_rouge.git'
            }
        }

        stage('Initialisation de Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'terraform init'
                }
            }
        }

        stage('Plan Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'terraform plan'
                }
            }
        }

        stage('Application de Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
