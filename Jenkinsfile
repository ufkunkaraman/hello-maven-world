pipeline {
  agent any
  stages {
    stage('Begin Ci/Cd (Developer Confirmation)') {
      parallel {
        stage('Begin Ci/Cd (Developer Confirmation)') {
          agent {
            node {
              label 'test-node'
            }

          }
          environment {
            confirm_ip = '192.168.1.39'
          }
          steps {
            echo 'Developer Start Ci/Cd / Print Message'
            sh 'echo "hi"'
            sh 'echo ${confirm_ip}'
          }
        }

        stage('get token') {
          agent {
            node {
              label 'test-node'
            }

          }
          steps {
            sh 'curl -X POST "http://$confirm_ip:5000/api/v1/security/login" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\\"password\\":\\"admin\\",\\"provider\\":\\"db\\",\\"refresh\\":true,\\"username\\":\\"admin\\"}" > auth.token'
          }
        }

        stage('add confirmation') {
          agent {
            node {
              label 'test-node'
            }

          }
          steps {
            sh 'curl -X POST "http://127.0.0.1:5000/api/v1/developerconfirm/" -H  "accept: application/json" -H  "Content-Type: application/json" -d "{\\"info\\":\\"string\\",\\"name\\":\\"string\\",\\"stage\\":\\"string\\"}" > developerbegincicd'
          }
        }

        stage('control confirmation') {
          agent {
            node {
              label 'test-node'
            }

          }
          steps {
            sh '''curl -X GET "http://127.0.0.1:5000/api/v1/developerconfirm/2?q=%7B%0A%20%20%22columns%22%3A%20%5B%0A%20%20%20%20%22name%22%2C%0A%22stage%22%0A%20%20%5D%2C%0A%20%20%22keys%22%3A%20%5B%0A%20%20%20%20%22show_columns%22%0A%20%20%5D%0A%7D" -H  "accept: application/json"
'''
          }
        }

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
  environment {
    confirm_ip = '192.168.1.39'
  }
}