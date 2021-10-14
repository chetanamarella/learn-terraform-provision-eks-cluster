pipeline {
  agent any 
  
  stages {
    stage('Git Checkout') {
      steps {
        git 'https://github.com/chetanamarella/learn-terraform-provision-eks-cluster.git' 
        //sh 'cd learn-terraform-provision-eks-cluster'
      }
    }
    
    stage('Terraform Init') {
      steps {
        sh 'terraform init -upgrade'
      }
    }
    /*
    stage('Terraform Apply') {
      steps {
        withAWS(credentials: 'aws', region: 'us-east-2') {
          sh 'terraform apply --auto-approve'
        }
      }
    } */
    
    stage('Terraform action') {
      steps {
        withAWS(credentials: 'aws', region: 'us-east-2') {
        echo "The action performed is ${Action}"
        sh 'terraform ${Action} --auto-approve'
        sh 'cd /var/lib/jenkins/workspace/terraform-eks'  
        sh 'aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)'  
          
        }
      }
    } 
  }
}

      
