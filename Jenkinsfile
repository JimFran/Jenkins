pipeline {
    
    agent any
    
    stages {

        
        stage("Clon GitHub Ansible repository"){
            
            steps{
                
                git 'https://github.com/JimFran/ansible'
                
            }
            
        }
        
        
        stage('PULL IMAGE'){
        
            steps{
            
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'ubuntu2', installation: 'ansible', inventory: 'hosts', playbook: 'Pull_images.yml'
              
            }
        }
        
        stage('CREATE IMAGE'){
        
            steps{
            
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'ubuntu2', installation: 'ansible', inventory: 'hosts', playbook: 'Create_image.yml'
              
            }
        }
        
        
        stage('CREATE CONTAINER'){
        
            steps{
            
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'ubuntu2', installation: 'ansible', inventory: 'hosts', playbook: 'Create_container.yml'
              
            }
        }
        
        stage('VALIDATOR'){
        
            steps{
            
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'ubuntu2', installation: 'ansible', inventory: 'hosts', playbook: 'validator.yml'
              
            }
        }
        
    }
}
