pipeline {
    agent {
label "agent1"
}
    parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'develop', name: 'BRANCH', type: 'PT_BRANCH', quickFilterEnabled: true
  }
  options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        stage('copy') {
            steps {
                sh "cp -r /home/jenkins/workspace/test_master/* /var/www/html"
            }
        }

    }
}
