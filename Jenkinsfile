pipeline {
    // add your slave label name
    agent { label 'my_first_jenkin_slave'}
    tools{
        maven 'maven-test'
    }
    stages {
        stage ('Checkout_SCM') {

            steps {
          	    
	     checkout scm
            }
        }

        stage ('Maven_Build') {

            steps {
               sh 'mvn clean package'
            }
        }
        
        stage ('Deploy_Tomcat') {

            steps {
	      sshagent(['my-tomcat-key']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@15.207.84.156:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}
