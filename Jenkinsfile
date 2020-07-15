pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''cd /home/yinyong

rm -rf web;

svn co https://172.16.0.58:7777/svn/project/xwtd/trunk/web
'''
        sh '''cd /home/yinyong/web/webinner
sh module_build.sh'''
        sh '''file=$(find /home/yinyong/web/webinner -name *.tar.gz)

cd /home/yinyong


./sshpass -p bigdata@71 scp -o StrictHostKeyChecking=no /home/yinyong/web/webinner/${file##*/} root@172.16.1.71:/home/zz

 '''
      }
    }

    stage('Install') {
      steps {
        sh '''echo "#!/bin/bash
yum -y install expect
expect -c "
spawn scp -r /home/yinyong/web/webinner/xwtd-webinner-install-20200715.tar.gz root@172.16.1.71:/home/zzz
expect {
    \\"*assword\\" 
                {
                    set timeout 300; 
                    send \\"bigdata@71\\r\\";
                }
    \\"yes/no\\" 
                {
                    send \\"yes\\r\\"; exp_continue;}
                }
expect eof" > scp.sh


'''
      }
    }

  }
}