node {
  stage('SCM') {
    checkout scm
  }
  stage('Test') {
    sh '''#!/bin/bash
    cd /var/lib/jenkins/workspace/django_project/project_env/bin/activate'''
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}

