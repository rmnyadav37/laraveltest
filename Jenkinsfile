pipeline{
	agent{ label 'agent2'}
	stages{
	    stage('SonarQube Analysis') {
    	    def scannerHome = tool 'sonarqubescanner-5.0.1';
    	    withSonarQubeEnv() {
      	    sh "${scannerHome}/bin/sonar-scanner"
    	    }
  	}
	    stage('Deploy') {
            steps {
                sh "cp -r /home/jenkins/workspace/firstproject/* /var/www/html"
                echo 'Hello stage1'
	    }	
	    }

            stage('Sucess') {
		    echo "Pipeline success"
	    }
	}
}
		
			
