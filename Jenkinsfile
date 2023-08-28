node{
    
    
echo "Jenkins Home dir is: ${env.JENKINS_HOME}"
echo "Job name is: ${env.BUILD_NUMBER}"
echo "Build number is: ${env.BUILD_NUMBER}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name:'maven3.9.4'

stage('checkOutcode'){
git branch: 'development', credentialsId: '6c4d860c-359e-4cc9-9bdc-ac9bb629223a', url: 'https://github.com/veeresh996/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsInotNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeploAppIntoTomcatServer'){
sshagent(['67787e46-fda4-4934-a0aa-1355ee0d4109']) {
      sh"scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.34.137:/opt/apache-tomcat-9.0.78/webapps/"
}
}
*/

}
