pipeline
{
agent any
stages
{
  stage('scm checkout')
   {
     steps 
     { 
      git 'https://github.com/Pallavi2899/maven-project.git' 
     }
   }
  stage ('validate')
  {
    steps {
      withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn validate'
}
  }
  }
  stage('code compile')
   {
     steps 
     { 
      withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn compile'
     }
   }
   }
   stage('package the code')
   {
     steps 
     { 
      withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn clean package'
     }
   }
          }
   stage('Deploy the code')
   {
     steps 
     { 
      sshagent(['DEVCICD']) {
    
sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@18.212.197.48:/usr/share/tomcat/webapps'
     }
   }
          }       
}
}