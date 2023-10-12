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
            steps {
                   sh "mvn clean package"
                }
            }
        stage ("Dev Deploy") {
            steps {
               echo "Deploy to Dev"     
            }
        }  
        stage ("Test Deploy") {
            steps {
               echo "Deploy to Test"     
            }
        }
        stage ("prod Deploy") {
            steps {
               echo "Deploy to prod"     
            }
        }     
    }
}
