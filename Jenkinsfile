pipeline {
	agent any
	stages {
		stage ('Checkout') {
			steps {
			git branch:'master', url: 'https://github.com/wyvernk/JenkinsDependencyCheckTest.git'
			}
		}

		 stage('OWASP Dependency-Check Vulnerabilities') {
		  steps {
			 dependencyCheck additionalArguments: ''' 
						-o './'
						-s './'
						-f 'ALL'
						--prettyPrint
						--noupdate
						''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		  }
		}
		
	}
	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
