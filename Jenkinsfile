pipeline {
  agent any
  stages {
    stage('Build') {
      post {
        failure {
          emailext(subject: 'Project Integration', body: 'There was an error integrating your project!', from: 'ha_rezgui@esi.dz', to: 'hn_messaoudi@esi.dz')
        }

      }
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

    stage('Slack Notification') {
      steps {
        slackSend(baseUrl: 'https://hooks.slack.com/services/', token: 'T01MCAEM4BD/B01SL1KGL1K/qZzhVP0W028lWAsbhNczi979', teamDomain: 'equipededevel-igz2777', message: 'The project is updated!', channel: 'ogl')
      }
    }

  }
}