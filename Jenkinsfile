pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/docs/**'
        archiveArtifacts 'build/test-results/**'
      }
    }

    stage('Mail Notification') {
      steps {
        emailext(subject: 'Project Integration', body: 'The project has been integtated successfully!', from: 'ha_rezgui@esi.dz', to: 'hn_messaoudi@esi.dz')
      }
    }

  }
}