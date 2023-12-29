pipeline {
    agent { label "agent2" }
    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        
        }
        stage ("SonarQube Gatekeeper") {
         steps {
            script {
               STAGE_NAME = "SonarQube Gatekeeper"

               if (BRANCH_NAME == "develop") {
                  echo "In 'develop' branch, skip."
               }
               else { // this is a PR build, fail on threshold spill
                  def qualitygate = waitForQualityGate()
                  if (qualitygate.status != "OK") {
                     error "Pipeline aborted due to quality gate coverage failure: ${qualitygate.status}"
              } 
           }
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

