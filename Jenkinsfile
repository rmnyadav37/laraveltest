pipeline {
    agent {
label "agent1"
}

    stages {
        stage('copy') {
            steps {
                sh "cp -r /home/jenkins/workspace/test_master/* /var/www/html"
            }
        }

    }
}
