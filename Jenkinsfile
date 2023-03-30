pipeline {
    agent any
    tools {
        terraform 'terraform'
        }
stages {
        stage('Git Checkout') {
            steps {
                git branch: 'devops', credentialsId: 'Git', url: 'https://github.com/nazeekesen016/terraformjenkins'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform Plan') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIA3POQ7IP3C67HDRP3', credentialsId: 'aws',  secretKeyVariable: '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']]) 
                {
                sh 'terraform plan'
                }
            }
            }
        stage('Terraform Apply') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIA3POQ7IP3C67HDRP3', credentialsId: 'aws', secretKeyVariable: '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']]) 
                {
                
                sh 'terraform apply --auto-approve'
                }
            }  
        }
    }
 }
