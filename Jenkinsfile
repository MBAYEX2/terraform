pipeline {
    agent any

    environment {
        TERRAFORM_DIR = 'terraform_fil_rouge/Terraform_Fil_Rouge'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/votre-utilisateur/terraform_fil_rouge.git'
            }
        }

        stage('Init Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'terraform init'
                }
            }
        }

        stage('Plan Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'terraform plan -out=tfplan'
                }
            }
        }

        stage('Apply Terraform') {
            steps {
                dir("${env.TERRAFORM_DIR}") {
                    sh 'terraform apply -auto-approve tfplan'
                }
            }
        }
    }

    post {
        failure {
            echo 'Le pipeline a échoué.'
        }
        success {
            echo 'Le pipeline a été exécuté avec succès.'
        }
    }
}
