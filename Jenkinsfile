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
                sh 'cd my-app' 
                sh 'npm install --force'
            }
        }
        
        stage('build'){
            steps {

          script{
          //sh "npm -v "
          //sh "npm install --legacy-peer-deps"
            //sh 'cd my-app'
            sh "ansible-playbook my-app/ansible/build.yml -i my-app/ansible/inventory/host.yml"
               }
            }
                    }
                    
        }
        
        
}
