pipeline {
  agent {
    label 'icp-int'
  }

  stages {
    stage('Dependencies') {
      steps {
        sh 'yarn install'
      }
    }
    stage('Check Formatting') {
      sh 'yarn check-formatting'
    }
    stage('Lint') {
      sh 'yarn lint'
    }
    stage('Depcheck') {
      sh 'yarn depcheck'
    }
    stage('Run tests') {
      sh 'yarn test'
    }
    stage('Build') {
      sh 'yarn build'
    }
    stage('Docker Build') {
      sh "docker build -t 'docker-test/app:v1.0.0' ."
    }
  }
}