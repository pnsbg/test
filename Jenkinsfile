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
               sh ("/usr/local/bin/docker rm dge -f")
               sh ("/usr/local/bin/docker run --name dge -v ${WORKSPACE}:/app dge_report:latest write_all ${sprint} --version=${version}")
           }
        }
       stage('write') {
           steps {
               script {
                   def date = new Date()
                   def data = "Hello World\nSecond line\n" + date
                   writeFile(file: 'zorg.txt', text: data)
                   sh "ls -l"
              }
          }
        }
    }
    post {
      always {
        archiveArtifacts artifacts: 'rel_ver_tar/*.xlsx', fingerprint: true
        sh ("/usr/local/bin/docker rm dge -f")
      }
    }
}