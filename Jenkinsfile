node
{
    def mavenHome = tool name: "maven3.8.1"
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

 stage('CheckoutCode')
 {
 git branch: 'development', credentialsId: 'b069c675-1610-416f-9b17-683c8a4960cc', url: 'https://github.com/saikumar2255/maven-web-application.git'
 }
 stage('Build')
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
  /*
 stage('ExecuteSonarQubeReport')
 {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 stage('UploadArtifactsintoNexus')
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 stage('DeployAppintoTomcatServer')
 {
 sshagent(['fc5b09fc-9d7a-4195-ba47-0f6d0c0c0573']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.126.181.159:/opt/apache-tomcat-9.0.45/webapps/"
}
}
*/
stage('SendEmailNotification')
{
emailext body: '''Build Over....
Regards,
sai''', subject: 'Build Over....', to: 'sai26234@gmail.com,sowjanyag873@gmail.com'
 }
}
