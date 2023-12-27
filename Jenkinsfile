node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner-5.0.1';
    withSonarQubeEnv() {
      sh "/var/lib/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqubescanner-5.0.1/bin
/bin/sonarqubescanner-5.0.1"
    }
  }
}
