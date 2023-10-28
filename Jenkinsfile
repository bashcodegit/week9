node {
  stage('SCM') {
    checkout scm
  }
  stage('Test') {
    echo 'Application Testing'
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
