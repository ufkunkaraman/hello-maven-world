pipeline {
  agent any
  stages {
    stage('Begin Ci/Cd (Developer Confirmation)') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        echo 'Developer Start Ci/Cd / Print Message'
        sh 'echo "hi"'
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

    stage('Test  (Tester Confirmation)') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        echo 'hi'
      }
    }

    stage('Deploy (Developer Confirm )') {
      steps {
        echo 'test'
      }
    }

    stage('Deploy') {
      parallel {
        stage('install python lib') {
          steps {
            sh 'echo "deploy"'
            sh 'pip install -r requirements.txt'
          }
        }

        stage('work python') {
          steps {
            sh 'python3 app.py'
          }
        }

      }
    }

  }
}