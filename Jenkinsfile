pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        sh 'gradle javadoc'
      }
    }

  }
}