pipeline{
 agent any
   stages{
    stage("Checkout"){
           steps{
                   checkout scm
                            }
                       }
                     stage("Build"){
                                 steps{
                             sh '/home/harsh/Documents/apache-maven-3.9.6/bin/mvn install'
                }
             }
        stage("Deployment"){ 
            steps{ 
                 sh 'cp target/Fan.war /home/harsh/Documents/apache-tomcat-9.0.88/webapps'
           }
      }
   }
 }
