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

