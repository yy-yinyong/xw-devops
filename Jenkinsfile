pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sleep 1
        sh '''cd /home/yinyong

rm -rf web;

svn co https://172.16.0.58:7777/svn/project/xwtd/trunk/web
'''
      }
    }

  }
}