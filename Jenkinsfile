pipeline {
  agent any
  stages {
    stage('hi') {
      steps {
        echo 'hi'
        sh 'cat pom.xml'
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

  }
}