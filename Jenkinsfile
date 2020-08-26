pipeline {
  agent any
  stages {
    stage('BEGIN OR NOT') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        echo 'hi'
        sh 'cat pom.xml'
        input(message: 'GO?', id: 'No', ok: 'YES')
        timeout(time: 10, activity: true) {
          input(message: 'go ', id: 'go ', ok: 'go ')
        }

      }
    }

    stage('Build') {
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
            sh 'cat Jenkinsfile'
            sh ''' cat pom.xml
'''
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
            sh 'cat pom.xml'
            sh 'uname -a'
            sh 'whoami'
          }
        }

        stage('build') {
          agent {
            docker {
              image 'maven:3.5.3-jdk-8-slim'
            }

          }
          steps {
            sh '''echo "Building the server code...";
mvn --version ;
mkdir -p targer ; 
touch "target/server.war";'''
          }
        }

      }
    }

    stage('Test or not') {
      agent {
        node {
          label 'test-1'
        }

      }
      steps {
        echo 'hi'
      }
    }

    stage('Test') {
      steps {
        echo 'test'
      }
    }

    stage('deploy or not ') {
      steps {
        input(message: '1', id: '1', ok: '1')
      }
    }

  }
}