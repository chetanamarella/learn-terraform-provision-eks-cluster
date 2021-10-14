pipeline {
  agent any 
  
  stages {
    stage('Git Checkout') {
      steps {
        git 'https://github.com/chetanamarella/learn-terraform-provision-eks-cluster.git' 
        sh 'cd learn-terraform-provision-eks-cluster'
      }
    }
    
    stage('Terraform Init') {
      steps {
        sh 'terraform init'
      }
    }
    
    stage('Terraform Apply') {
      steps {
        sh 'terraform apply'
      }
    }
    
   /* stage('Terraform action') {
      steps {
        echo "The action performed is ${Action}"
        sh 'terraform ${action} --auto-approve'
      }
    } */
  }
}
      
