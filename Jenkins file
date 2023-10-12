pipeline {
    agent any
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
                    sshagent(['tomcat-dev']) {
                    // copy war file to tomcat
                     sh "scp  -o StrictHostKeyChecking=no target/max-healthcare.war ec2-user@172.31.0.179:/opt/tomcat9/webapps"
                    // stop tomcat
                    sh "ssh  ec2-user@172.31.0.179 /opt/tomcat9/bin/shutdown.sh"
                    // start tomcat
                    sh "ssh  ec2-user@172.31.0.179 /opt/tomcat9/bin/startup.sh"
                    }
                }
                
            }
       }
}
