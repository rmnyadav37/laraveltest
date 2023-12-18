pipeline {
    agent {
        label "agent1"
    }

    stages {
        stage('copy') {
            steps {
                sh "cp -r /home/jenkins/workspace/pipeline/* /var/www/html"
                echo 'Hello stage1'
            }
        }
        stage('stage2') {
            steps {
                echo 'Hello stage2'
            }
        }
        stage('stage3') {
            steps {
                echo 'Hello stage3'
            }
        }
        stage('stage4') {
            steps {
                echo 'Hello stage4'
            }
        }
        stage('stage5') {
            steps {
                echo 'Hello stage5'
            }
        }
        stage('stage6') {
            steps {
                echo 'Hello stage6'
            }
        }
    }
}
