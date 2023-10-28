node {
  stage('SCM') {
    checkout scm
  }
  stage('Test') {
    steps {
      script {
        def venv = "/var/lib/jenkins/workspace/django_project/project_env/bin/activate"
        sh "source $venv && python3 manage.py test"
      }
    }
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}

