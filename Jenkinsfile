pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        node(label: 'master') {
          sh '''
            echo $hostname
            echo $hostname
            echo $WORKSPACE
            echo $WORKSPACE
            echo ${JOB_NAME}'''
        }
        
        archiveArtifacts(artifacts: '**', defaultExcludes: true)
      }
    }
  }
}
