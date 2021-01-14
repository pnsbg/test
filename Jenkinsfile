#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library
def (version, sprint) = "${PROBA}".split(",")


pipeline {
    agent {
        label "master"
    }
    stages {
        stage('Run conteiner') {
           steps {
               sh ("/usr/local/bin/docker run  -v ${WORKSPACE}:/app dge_report:latest write_all ${sprint} --version=${version}")
           }
        }
    }
    post {
      always {
        archiveArtifacts artifacts: '*.xlsx', fingerprint: true
      }
    }
}