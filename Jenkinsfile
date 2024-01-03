pipeline {
    agent { label "agent2" }
    
    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'sonarqubescanner-5.0.1'
                    withSonarQubeEnv() {
                        // Run SonarQube analysis
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage('Quality Gate') {
            steps {
                script {
                    timeout(time: 30, unit: 'MINUTES') {
                        waitForQualityGate abortPipeline: true
                    }
                }
            }
        }

        stage('Copy') {
            steps {
                script {
                    try {
                        sh "cp -r /home/jenkins-agent/workspace/firstproject/* /var/www/html"
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
