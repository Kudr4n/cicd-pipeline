pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('Build image') {
      steps {
        sh 'docker build -t kudran_image '
      }
    }

    stage('Push image') {
      steps {
        sh '''docker login --username ${env.login} --password-stdin ${env.password}
'''
        sh 'docker image tag kudran:latest'
        sh 'docker image push'
      }
    }

  }
}