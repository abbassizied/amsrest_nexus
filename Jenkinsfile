pipeline {
  agent any
  tools {
    maven 'maven383'
  }

  stages {
    stage('Build du Projet') {
      steps {
        sh 'mvn clean install -DskipTests'
      }
    }

    stage('Déposer artifact vers repo nexus') {

      steps {

        script {

          nexusArtifactUploader artifacts: [

              [
                artifactId: 'ams_rest',
                classifier: '',
                file: 'target/ams_rest-0.0.1-SNAPSHOT.jar',
                type: 'jar'

              ]

            ],

            credentialsId: 'nexus_cred',
            groupId: 'com.sip',
            nexusUrl: 'localhost:8081',
            nexusVersion: 'nexus3',
            protocol: 'http',
            repository: 'ams_repo',
            version: '0.0.1-SNAPSHOT'

        }

      }

    }

  }
}


