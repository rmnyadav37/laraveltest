node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner-5.0.1';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin
/bin/sonarqubescanner-5.0.1"
    }
  }
}
