#!/usr/bin/env groovy

@Grab(group='org.jsoup', module='jsoup', version='1.10.1')
import org.jsoup.Jsoup
import org.jsoup.nodes.Document
import org.jsoup.nodes.Element
import org.jenkinsci.plugins.workflow.libs.Library

def (old, version, sprint) = "${PROBA}".split(",")
Document doc = Jsoup.connect("https://artifactory.k8s.starsops.com/artifactory/devops-amelco-releases/ats").userAgent("Mozilla").get();
for (Element e: doc.select("a.question-hyperlink")) {
    System.out.println(e.attr("abs:href"));
    System.out.println(e.text());
    System.out.println();
}

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