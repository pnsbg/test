#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library

def buildUser = getBuildUser()

node('Slave01') {
    currentBuild.description = "${ENVIRONMENT} ${COMPONENT}"
    env.STARTED_BY = "${buildUser}"
    env.SLACK_URL = 'https://stars-sports.slack.com/services/hooks/jenkins-ci/'
    env.SLACK_CHANEL = 'tf-env'
    env.SLACK_TOKEN = 'tf-env-slack'
    env.DEFAULT_TERRAFORM_BRANCH = 'master'
    env.TERRAFORM_REPO_URL = 'ssh://git@lonstash.csr.pstars:8073/deo_moved_to_sts_bb/environments_terraform.git'
    env.DEFAULT_SPECS_BRANCH = 'master'
    env.SPECS_REPO_URL = 'ssh://git@lonstash.csr.pstars:8073/deo_moved_to_sts_bb/environments_spec.git'
    env.GIT_SPECS_BRANCH = 'master'
    env.VAULT_URL = "https://vault.k8s.starsops.com/"
    env.HELM_BRANCH = 'master'
    env.HELM_REPO_URL = 'ssh://git@lonstash.csr.pstars:8073/deo_moved_to_sts_bb/ats-infra-helm-charts.git


    stage('Test Env') {
        step('proba') {
          echo "Proba VAR ${PROBA}"
          sh 'printenv'
        }
    }
}