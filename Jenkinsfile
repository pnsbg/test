#!/usr/bin/env groovy


import org.jenkinsci.plugins.workflow.libs.Library
def (version, sprint) = "${PROBA}".split(",")


pipeline {
    agent {
        label "master"
    }
    stages {
       stage('write') {
           steps {
               script {
                   def date = new Date()
                   def data = '''old version: 0.3746.1496.2 
                                 
                                         ATS:
                                                  ATS (release-pokerstars-0.3746.1496.2_20201113_1217.tar.gz): ver 0.3746.1496.2''' + date
                   writeFile(file: 'zorg.txt', text: data)
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