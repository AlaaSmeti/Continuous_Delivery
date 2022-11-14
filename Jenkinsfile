pipeline {
    agent any
    stages{
       
        stage('Checkout GIT') {
            steps {
                echo 'Pulling branch from Git' ;
                git branch: 'main',
                url: 'https://github.com/AlaaSmeti/Continuous_Delivery.git'
            }
        }
        stage('NPM INSTALL') {
            steps{
            
                sh 'npm install --force'
            }
        }
        
        stage('BUILD'){
            steps {

          script{
            sh "echo admin | sudo ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
               }
            }
                    }
         stage('DOCKER') {
            steps{
            	script{
                sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }           
         stage('DOCKER-HUB') {
            steps{
            	script{
                sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
                }
            }
        }    
        stage('STARTING MONITORING') {
            steps{
            	script{
                sh "echo admin | sudo -S docker-compose up -d"
                }
            }
        }                  
                    
        }
        
        
}
