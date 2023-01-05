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
              echo 'deploy to Nexus..'
              pom = readMavenPom file: "pom.xml";
             // pom = readMavenPom file: "https://github.com/youssefjeh/Maven-deploy-to-Nexus-using-Jenkins/blob/main/pom.xml";
              filesByGlob = findFiles(glob: "target/*.${pom.packaging}");
              echo "${filesByGlob[0].name} ${filesByGlob[0].path} ${filesByGlob[0].directory} ${filesByGlob[0].length} ${filesByGlob[0].lastModified}"
              artifactPath = filesByGlob[0].path;
              artifactExists = fileExists artifactPath;
              if(artifactExists) {
                  echo "*** File: ${artifactPath}, group: ${pom.groupId}, packaging: ${pom.packaging}, version ${pom.version}";
                  nexusArtifactUploader(
                                      nexusVersion: NEXUS_VERSION,
                                      protocol: NEXUS_PROTOCOL,
                                      nexusUrl: NEXUS_URL,
                                      groupId: pom.groupId,
                                      version: pom.version,
                                      repository: NEXUS_REPOSITORY,
                                      credentialsId: NEXUS_CREDENTIAL_ID,
                                      artifacts: [
                                          [artifactId: pom.artifactId,
                                          classifier: '',
                                          file: artifactPath,
                                          type: pom.packaging],
                                          [artifactId: pom.artifactId,
                                          classifier: '',
                                          file: "pom.xml",
                                          type: "pom"]
                                      ]
                                  );
                              } else {
                                  error "*** File: ${artifactPath}, could not be found";
                                }
        }
      }
    }
  }
}
