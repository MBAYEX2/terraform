pipeline {
    agent any

    stages {
        stage('Checkout du code') {
            steps {
                git branch: 'main', url: 'https://github.com/fatou0409/terraform_fil_rouge.git'
            }
        }

        stage('Initialisation de Terraform') {
            steps {
                dir('Terraform_Fil_Rouge') {
                    bat 'terraform init'
                }
            }
        }

        stage('Plan Terraform') {
            steps {
                dir('Terraform_Fil_Rouge') {
                    bat 'terraform plan'
                }
            }
        }

        stage('Application de Terraform') {
            steps {
                dir('Terraform_Fil_Rouge') {
                    bat 'terraform apply -auto-approve'
                }
            }
        }
    }
}
