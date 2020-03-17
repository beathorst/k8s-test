pipeline {

  agent any

  environment {
    APP_NAME = "k8s-test"
  }

  stages {
    stage('Test') {
      steps {
        sh "echo test -- ${APP_NAME}"
      }
    }
    stage('Build and push image with Container Builder') {
      steps {
        sh "echo Build and push image -- ${APP_NAME}"
      }
    }
    stage('Deploy Develop') {
      // Canary branch
      when { branch 'develop' }
      steps {
        sh "echo Deploy Develop -- ${APP_NAME}"
      }
    }
    stage('Deploy Production') {
      // Production branch
      when { branch 'master' }
      steps{
        sh "echo Deploy Production -- ${APP_NAME}"
      }
    }
    stage('Deploy Branches') {
      // Developer Branches
      when {
        not { branch 'master' }
        not { branch 'develop' }
      }
      steps {
        sh "echo Deploy Developer Branches -- ${APP_NAME}"
      }
    }
  }
}
