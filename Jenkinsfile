pipeline {
  agent any
  stages {
    stage('hi') {
      steps {
        echo 'hi'
      }
    }

    stage('meavenbuuild') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        sh 'echo "merhaba" > /home/netgsm/test'
      }
    }

  }
}