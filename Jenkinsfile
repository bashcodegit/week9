node {
  stage('SCM') {
    checkout scm
  }
  stage('Test') {
    echo 'Test App'
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}

