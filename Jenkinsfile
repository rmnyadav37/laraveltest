node {
  agent{
    labels "agent2"
  }
  stages{
    stage('SonarQube Analysis') {
      def scannerHome = tool 'sonarqubescanner-5.0.1';
      withSonarQubeEnv() {
        sh "${scannerHome}/bin/sonar-scanner"
    }
  }
  
    stage('deploy'){
      sh "ls -al"
      sh "cp -r /home/jenkins-agent/workspace/firstproject/* /var/www/html/"
     
  }
}
