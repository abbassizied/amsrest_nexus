pipeline {
  agent any
  tools {
    maven 'maven383'
  }

  stages {
    stage('build') {
      steps {
        sh 'mvn clean install -DskipTests'
      }
    }

    stage('deploy to Nexus') {

      steps {

        script {

          nexusArtifactUploader(

            artifacts: [
              // Artifact generated such as .jar, .ear and .war files.
              [artifactId: 'ams_rest',
                classifier: '',
                file: 'target/ams_rest-0.0.1-SNAPSHOT.jar',
                type: 'jar']
            ],

            credentialsId: 'nexus_cred',
            groupId: 'com.sip',
            nexusUrl: 'localhost:8081',
            nexusVersion: 'nexus3',
            protocol: 'http',
            repository: 'ams_repo',
            version: '0.0.1-SNAPSHOT'
          );
        }

      }

    }

  }
}


