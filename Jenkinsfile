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
        }
      }
    }

    stage("build docker image") {
      
      steps {
        script{
          echo "build docker img"
        }
      }
    }
   }
  }
