@Library('jenkins-SL') 
def gv
pipeline {
  agent any
  tools {
    maven 'maven'
  }
  environment {
    NEXUS_VERSION = "nexus3"
    NEXUS_PROTOCOL = "http"
    NEXUS_URL = "20.199.22.41:8081"
    NEXUS_REPOSITORY = "MavenYJ-central"
    NEXUS_CREDENTIAL_ID = "NEXUS_CRED"
  }
  stages {
    stage("build Jar") {
      steps {
        script{
            buildJar()
        }
      }
    }

    stage("Deploy") {
      steps {
        script{
              DeployNexus()
        }
      }
    }
  }
}
