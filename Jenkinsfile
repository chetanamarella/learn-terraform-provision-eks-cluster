pipeline {
  agent any 
  
  stages {
    stage('Git Checkout') {
      steps {
        git 'https://github.com/chetanamarella/learn-terraform-provision-eks-cluster.git' 
      }
    }
    
    stage('Terraform Init') {
      steps {
        sh 'terraform init -upgrade'
      }
    }
    
    stage('Terraform Plan') {
      steps {
        withAWS(credentials: 'aws', region: 'us-east-2') {
          sh 'terraform plan'
        }
      }
    } 
    
    stage('Terraform action') {
      steps {
        withAWS(credentials: 'aws', region: 'us-east-2') {
        echo "The action performed is ${Action}"
        sh 'terraform ${Action} --auto-approve'
        
        /*sh '''#!/bin/bash
          if [ ${Action} == "apply" ]; then
        
           cd /var/lib/jenkins/workspace/terraform-eks  
           aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name) 
          fi 
          
          ''' */
        }
      }
    } 
  }
}

      
