@Library('jenkins-SL') 
def gv
pipeline {
  agent any
  tools {
    maven 'maven'
  }
  
  stages {
    
    stage("build Jar") {
      
      steps {
        script{
            echo "build jar"
            buildJar()
        }
      }
    }

    stage("Deploy") {
      
      steps {
        script{
          withCredentials([usernamePassword(credentialsId: 'nexus credentials',usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD]) {
            sh "mvn deploy -DaltDeploymentRepository=releases::default::http://20.199.22.41:8081/repository/release-maven/ -Dusername=${USERNAME} -Dpassword=${PASSWORD}"
          }
        }
      }
    }
   }
  }
