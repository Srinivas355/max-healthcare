pipeline {
    agent any
    parameters {
         choice choices: ['dev', 'test', 'prod'], description: 'choose the environment to deploy', name: 'envname'
     }
     stages{
        stage ("git checkout"){
            steps {
                 git branch: 'main', credentialsId: 'Git-hub', url: 'https://github.com/Srinivas355/max-healthcare.git'
                }
        }
        stage ("maven build") {
            when{
               expression { params.envname == "dev" }
            } 
            steps {
                   sh "mvn clean package"
                }
            }
        stage ("Dev Deploy") {
            when{
               expression { params.envname == "dev" }
            }    
            steps {
              echo params.envname
              echo "Deploy to Dev"     
            }
        }  
        stage ("Test Deploy") {
             when{
               expression { params.envname == "test" }
            } 
            steps {
               echo "Deploy to Test"     
            }
        }
        stage ("prod Deploy") {
             when{
               expression { params.envname == "prod" }
            } 
            steps {
               echo "Deploy to prod"     
            }
        }     
    }
}
