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
            sh ''';echo "merhaba" > /home/netgsm/test
echo """To create the docker group and add your user:

    Create the docker group.

    $ sudo groupadd docker

    Add your user to the docker group.

    $ sudo usermod -aG docker $USER

    Log out and log back in so that your group membership is re-evaluated.

    If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect.

    On a desktop Linux environment such as X Windows, log out of your session completely and then log back in.

    On Linux, you can also run the following command to activate the changes to groups:

    $ newgrp docker 

"""'''
          }
        }

        stage('docker ps ') {
          agent {
            node {
              label 'test-1'
            }

          }
          steps {
            sh 'sudo docker ps'
          }
        }

      }
    }

  }
}