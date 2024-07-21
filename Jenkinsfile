pipeline {
	agent any
	stages {
        	stage('Build') {
            	steps {
                    	nodejs('nodejs'){
                        	sh 'npm install'
                    	}
            	}
        	}
	}
	stage('OWASP Dependency-Check Vulnerabilities') {
      steps {
        dependencyCheck additionalArguments: ''' 
                    -o './'
                    -s './'
                    -f 'ALL' 
                    --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
        
        dependencyCheckPublisher pattern: 'dependency-check-report.xml'
      }
    }
}
