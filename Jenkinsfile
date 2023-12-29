node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'sonarqubescanner-5.0.1';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
  agent{
    labels "agent2"
  }
  stage('SCM'){
    checkout scm
  }
  stage('copy'){
     sh "cp -r /home/jenkins/workspace/firstproject/* /var/www/html"
  }
}
