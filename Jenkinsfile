pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    sh 'python manage.py test' 
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool name: 'SonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation';
                    withSonarQubeEnv('YourSonarQubeServer') {
                        sh script: "${scannerHome}/bin/sonar-scanner", returnStatus: true
                    }
                }
            }
        }
    }
}
