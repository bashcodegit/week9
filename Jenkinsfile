node {
  stage('SCM') {
    checkout scm
  }
  stage('Test') {
    sh 'source /var/lib/jenkins/workspace/django_project/project_env/bin/activate'
    echo 'python3 manage.py test'
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
