pipeline {
  agent any
  stages {
    stage('Developer Start Ci/Cd or not') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        echo 'Developer Start Ci/Cd / Print Message'
      }
    }

    stage('Build-Test') {
      parallel {
        stage('install python lib') {
          agent {
            node {
              label 'test-1'
            }

          }
          steps {
            sh 'pip install -r requriements.txt'
          }
        }

        stage('work python') {
          agent {
            node {
              label 'test-1'
            }

          }
          steps {
            sh 'python3 app.py'
          }
        }

      }
    }

    stage('Tester Kontrol') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        echo 'hi'
      }
    }

    stage('Developer Confirm Deploy  project ') {
      steps {
        echo 'test'
      }
    }

    stage('Deploy') {
      steps {
        input(message: '1', id: '1', ok: '1')
      }
    }

  }
}