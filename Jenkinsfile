#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library


node('Slave01') {
    stage('Test Env') {
        step('proba') {
          echo "Proba VAR ${PROBA}"
          sh 'printenv'
        }
    }
}