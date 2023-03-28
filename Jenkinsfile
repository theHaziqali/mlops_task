pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps{
        checkout scm
      }
    }
    stage('Run') {
      steps {
        script {
          try {
            bat 'docker stop mlops_a2'
          } catch(err) {
            bat 'echo Container mlops_a2 Already Stopped'
          }
          try {
              bat 'docker rm mlops_a2'
          } catch(err1) {
            bat 'echo done'
          }
          try {
            bat 'docker image rm mlops_a2'
          } catch (err) {
            bat 'echo Image mlops_a2 Already Removed'
          }
          bat 'echo bingo!'
          bat 'docker build -t flaskapp .'
          echo 'Running docker image'
          bat 'docker run -p 3003:3003 -d flaskapp'
        }
      }
    }
  }
}
