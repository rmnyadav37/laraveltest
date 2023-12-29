pipeline {
    agent { label "agent2" }
    stages {
        
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonarqubescanner-5.0.1'
                    withSonarQubeEnv() {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
        stage('Copy') {
            steps {
                script {
                    try {
                        sh "cp -r /home/jenkins-agent/workspace/firstproject/* /var/www/html/"
                        echo 'Hello stage1'
                    } catch (Exception e) {
                        echo "Error copying files: ${e.message}"
                        currentBuild.result = 'FAILURE'
                        error("Error copying files")
                    }
                }
            }
        }
    }
}
