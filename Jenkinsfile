node
{
    def mavenHome=tool name:"maven3.6.3"
  stage('CheckoutCode') 
  {
      git branch: 'development', credentialsId: '7775f7b3-39c1-40d7-8b29-c7feea3286a5', url: 'https://github.com/dev-apps-jab/maven-web-application.git'
  }
  stage('BUILD')
  {
      sh "${mavenHome}/bin/mvn clean package"
  }
  /*
  stage('executesonarqubereport')
  {
     sh "${mavenHome}/bin/mvn sonar:sonar"
  }
  stage('uploadartifactsintonexus')
  {
      sh "${mavenHome}/bin/mvn deploy"
  }
  stage('DeployAPPintoTomcat')
  {
    sshagent(['ad0cbb9d-27f6-42ef-abac-610183594330']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.0.184.116:/opt/apache-tomcat-9.0.44/webapps/"
}  
  }
  */
  stage('sendemailnotification')
  {
      emailext body: '''BUILD-OVER scriptedway,


Regards,
devops.

''', subject: 'BUILD-OVER scriptedway', to: 'jabeenadevops@gmail.com'
  }
}
