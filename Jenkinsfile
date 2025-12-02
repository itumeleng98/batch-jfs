
pipeline {
  agent any
  options { timestamps() }
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Build') {
      steps {
        sh 'mvn -version'
        sh 'mvn -B clean package'
      }
    }
    stage('Archive JAR') {
      steps { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true }
    }
  }
  post {
    always { junit '**/target/surefire-reports/*.xml' }
  }
}
