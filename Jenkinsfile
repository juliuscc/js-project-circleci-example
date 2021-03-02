pipeline {
  agent {
    label 'icp-int'
  }

  stages {
    stage('Dependencies') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh 'yarn install'
        }
      }
    }

    stage('Check Formatting') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh 'yarn check-formatting'
        }
      }
    }
    stage('Lint') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh 'yarn lint'
        }
      }
    }
    stage('Depcheck') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh 'yarn depcheck'
        }
      }
    }
    stage('Run tests') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh 'yarn test'
        }
      }
    }
    stage('Build') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh 'yarn build'
        }
      }
    }
    stage('Docker Build') {
      steps {
        nodejs(nodeJSInstallationName: 'Node 14.x') {
          sh "docker build -t 'docker-test/app:v1.0.0' ."
        }
      }
    }
  }
}