pipeline {
  agent any 
  
  stages {
    stage('Git Checkout') {
      steps {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/chetanamarella/learn-terraform-provision-eks-cluster.git']]])
        sh 'cd learn-terraform-provision-eks-cluster'
      }
    }
    
    stage('Terraform Init') {
      steps {
        sh 'terraform init'
      }
    }
    
    stage('Terraform action') {
      steps {
        properties([parameters([choice(choices: ['apply --auto-approve', 'destroy --auto-approve'], name: 'Action')])])
      }
    }
  }
}
      
