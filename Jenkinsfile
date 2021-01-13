#!/usr/bin/env groovy

import org.jenkinsci.plugins.workflow.libs.Library



pipeline {
    agent {
        label "QA Worker"
    }

    environment {
        SALT_WRAPPER_JOB = "wrappers/salt_execute_wrapper_"
        STARTED_BY = "${buildUser}"
        VERSION = "First(Split("${PROBA}", " ")).Result"
    }
    
    stages {
        stage('Executing state') {
           steps {
             echo "Abe palen bastun sam kakvo da pravq ${PROBA}"
             echo "${STARTED_BY}"
             echo "${VERSION}"
           }
        }
    }
}  