pipeline {

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
        sh "Build and push image -- ${APP_NAME}"
      }
    }
    stage('Deploy Canary') {
      // Canary branch
      when { branch 'canary' }
      steps {
        sh "Deploy Canary -- ${APP_NAME}"
      }
    }
    stage('Deploy Production') {
      // Production branch
      when { branch 'master' }
      steps{
        sh "Deploy Production -- ${APP_NAME}"
      }
    }
    stage('Deploy Dev') {
      // Developer Branches
      when {
        not { branch 'master' }
        not { branch 'canary' }
      }
      steps {
        sh "Deploy Developer Branches -- ${APP_NAME}"
      }
    }
  }
}
