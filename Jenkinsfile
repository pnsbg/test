pipeline {
  agent {
    label "master"
  }
  stages {
    stage('test') {
      steps {
          sh '''
            echo $hostname
            echo $hostname
            echo $WORKSPACE
            echo ${JOB_NAME}'''
        }
        
        archiveArtifacts(artifacts: '**', defaultExcludes: true)
      }
    }
  }
