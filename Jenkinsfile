pipeline{
 agent any
parameters {
  choice choices: ['DEV', 'QA', 'UAT'], name: 'ENV'
}
triggers {
  pollSCM '* * * * *'
}
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
                 sh '''if [ $ENV = "DEV"  ]; then
cp target/Fan.war /home/harsh/Documents/apache-tomcat-9.0.88/webapps
echo "Deployed to DEV"
elif [ $ENV = "QA"  ]; then
cp target/Fan.war /home/harsh/Documents/apache-tomcat-9.0.88/webapps
echo "Deployed to QA"
elif [ $ENV = "UAT"  ]; then
cp target/Fan.war /home/harsh/Documents/apache-tomcat-9.0.88/webapps
echo "Deployed to UAT"
fi'''         }
      }
stage("Notification"){
    steps{
mail bcc: '', body: 'Build is in Process', cc: '', from: '', replyTo: '', subject: 'Build In Process', to: 'harshnathile@gmail.com'}
}
   }
 }
