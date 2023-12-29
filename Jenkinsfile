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
        stage("Quality gate") {
            steps {
                script {
                    // Wait for the Quality Gate check
                    def qg = waitForQualityGate()
                    // Add some logging or checks based on the 'qg' variable if needed
                    echo "Quality Gate status: ${qg.status}"
                    echo "Quality Gate ID: ${qg.id}"
                }
            }
        }

        stage('Copy') {
            steps {
                script {
                    try {
                        sh "cp -r /home/jenkins/workspace/firstproject/* /var/www/html"
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
