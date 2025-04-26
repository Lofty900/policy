pipeline {
  agent any

  environment {
    ARM_CLIENT_ID       = credentials('azure-client-id')
    ARM_CLIENT_SECRET   = credentials('azure-client-secret')
    ARM_SUBSCRIPTION_ID = credentials('azure-subscription-id')
    ARM_TENANT_ID       = credentials('azure-tenant-id')
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/Lofty900/policy.git'
      }
    }

    stage('Terraform Init') {
      steps {
        sh 'terraform init'
      }
    }

    stage('Terraform Plan') {
      steps {
        sh 'terraform plan -out=tfplan'
      }
    }

    stage('Terraform Apply') {
      steps {
        sh 'terraform apply -auto-approve tfplan'
      }
    }
  }
}