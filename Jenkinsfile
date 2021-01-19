#!/usr/bin/env groovy


import org.jenkinsci.plugins.workflow.libs.Library
def (old, version, sprint) = "${PROBA}".split(",")


pipeline {
    agent {
        label "master"
    }
    stages {
       stage('write') {
           steps {
               script {
                   def data = """old version: ${old} 
                                 
                                         ATS:
                                                  ATS (rel_ver): ver ${version}""" 
                   writeFile(file: 'manifest.txt', text: data)
                   sh "ls -l"
              }
          }
        }
        stage('Run conteiner') {
           steps {
               sh ("/usr/local/bin/docker rm dge -f")
               sh ("/usr/local/bin/docker run --name dge -v ${WORKSPACE}:/app dge_report:latest write_all ${sprint} --version=${version}")
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