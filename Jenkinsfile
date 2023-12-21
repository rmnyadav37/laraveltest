node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv('Scanner') {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
