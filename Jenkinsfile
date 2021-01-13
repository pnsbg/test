#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library



pipeline {
    agent {
        label "QA Worker"
    }

    environment {
        SALT_WRAPPER_JOB = "wrappers/salt_execute_wrapper_"
        STARTED_BY = "${buildUser}"
    }
    options {
        ansiColor('css')
    }
    stages {
        stage('make varaible') {
           steps {
             echo "ebati bastuna sam ${PROBA}"
           }
        }
    }
}