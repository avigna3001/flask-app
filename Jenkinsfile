pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/your-repo'
      }
    }
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Docker Build & Push') {
      steps {
        sh 'docker build -t yourname/app:latest .'
        sh 'docker push yourname/app:latest'
      }
    }
  }
}
