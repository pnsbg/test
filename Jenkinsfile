#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library

def buildUser = getBuildUser()

node('Slave01') {
    currentBuild.description = "${ENVIRONMENT} ${COMPONENT}"
    env.STARTED_BY = "${buildUser}"

    stage('Test Env') {
        step('proba') {
          echo "Proba VAR ${PROBA}"
          sh 'printenv'
        }
    }
}