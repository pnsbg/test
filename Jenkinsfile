#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library

def (version, sprint) = "${PROBA}".split(",")


pipeline {
    agent {
        label "QA Worker"
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Run conteiner') {
           steps {
               sh ("docker run  -v ${WORKSPACE}:/app dge_report:latest write_all ${sprint} --version=${version}")
           }
        }
    }
    post {
      always {
        archiveArtifacts artifacts: 'rel_ver_tar*.txt', fingerprint: true
      }
    }
}