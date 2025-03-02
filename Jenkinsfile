pipeline {
  agent any
  tools {maven 'MavenInstall'}
  parameters {
    string(name: 'BRANCH', defaultValue: 'master', description: 'Rama a compilar')
  }
  stages {
    stage('Checkout') {
      steps {
        script {
          if (fileExists('simple-java-maven-app')) {
            sh 'rm -rf simple-java-maven-app'
          }
          git branch: params.BRANCH, url: 'https://github.com/jenkins-docs/simple-java-maven-app.git'
        }
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
  }
}
