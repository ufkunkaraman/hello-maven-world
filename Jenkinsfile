pipeline {
  agent any
  stages {
    stage('hi') {
      steps {
        echo 'hi'
      }
    }

    stage('meavenbuuild') {
      parallel {
        stage('meavenbuuild') {
          agent {
            node {
              label 'test-1'
            }

          }
          steps {
            sh '''echo "merhaba" > /home/netgsm/test
'''
            sh 'whoami'
            sh 'whereis docker'
            sh 'which docker'
          }
        }

        stage('docker ps ') {
          agent {
            node {
              label 'test-1'
            }

          }
          steps {
            sh 'docker ps'
          }
        }

      }
    }

  }
}