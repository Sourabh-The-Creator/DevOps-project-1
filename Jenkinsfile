pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }

    stages {
        
        stage("Build Code"){
            steps{
               sh "mvn clean install"
            }
        }  
         stage("Deploy"){
            steps{
               sshagent(['ec2-deployer']) {
                  sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.7.68.118:/opt/tomcat/apache-tomcat-8.5.69/webapps"
                }
            }
        }  
        
    }
}
