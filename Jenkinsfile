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
               sh ("/usr/local/bin/docker rm jira -f")
               sh ("/usr/local/bin/docker run --name jira -v ${WORKSPACE}:/app dge_report:latest write_all ${sprint} --version=${version}")
           }
        }
      }
    post {
      always {
        archiveArtifacts artifacts: 'rel_ver_tar/*.xlsx', fingerprint: true
      }
      aborted {
        sh ("/usr/local/bin/docker rm jira -f")
      }
    }
}