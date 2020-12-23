pipeline {
  agent {
    label "master"
  }
  options {
      ansiColor("xterm")
  }

  environment {
      SALTENV =  "${BRANCH != "master" ? " saltenv=" + BRANCH + " " : " "}"
      PILLARENV = "${PILLAR_BRANCH != "master" ? " pillarenv=" + PILLAR_BRANCH + " " : " "}"
      ENVIRONMENTS = "${SALTENV + PILLARENV}"
      HOSTNAME =  "${HOSTNAME == null ? "\\*" : HOSTNAME}"
  }

  stages {
    stage('test') {
      steps {
          sh '''
            echo hostname
            echo hostname
            echo $WORKSPACE
            echo ${JOB_NAME}'''
          println("BASTUN")
        }
      }
    }
  }
