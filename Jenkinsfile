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
          }
}
