pipeline {
  agent any

  environment {
    AWS_ACCESS_KEY_ID     = credentials('aws')
    AWS_SECRET_ACCESS_KEY = credentials('aws')
  }

  stages {
    stage('Checkout') {
      steps {
        script {
          checkout scm
        }
      }
    }

    stage('Terraform Init') {
      steps {
        script {
          sh 'terraform init -backend-config=backend.tf'
        }
      }
    }

    stage('Terraform Apply') {
      steps {
        script {
          sh 'terraform apply -auto-approve'
        }
      }
    }
  }
}
