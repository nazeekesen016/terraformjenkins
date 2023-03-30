pipeline {
    agent any
    tools {
        terraform 'terraform'
        }
stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', credentialsId: 'forgit', url: 'https://github.com/nazeekesen016/terraformjenkins'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform Plan') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws',  secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
                {
                sh 'terraform plan'
                }
            }
            }
        stage('Terraform Apply') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACESS_KEY_ID', credentialsId: 'aws', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
                {
                
                sh 'terraform apply --auto-approve'
                }
            }
        }
    }
}
