pipeline {
  agent none
  stages {
    stage('') {
      steps {
        node(label: 'test1') {
          sh '''ssh-keygen -t rsa -f /home/daemon/.ssh/id_rsa -q -N ''
su -c "ssh-keygen -t rsa -f /home/daemon/.ssh/id_rsa -q -N ''" - daemon
echo $WORKSPACE
echo ${JOB_NAME}'''
        }
        
      }
    }
  }
}