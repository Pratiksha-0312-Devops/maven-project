pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/Pratiksha-0312-Devops/maven-project.git'
      }
    }

    stage('package job') //valiadte, compile, test & then package
    {
      steps {
          withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean package'
          }
        }
      }

    
    stage('deploy job') //valiadte, compile, test & then package
    {
      steps {
      sshagent(['DEVCICD']) {
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.10.93:/usr/share/tomcat/webapps'
        }


          }
        }
      }


    }
