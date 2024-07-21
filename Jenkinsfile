pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git url: 'https://github.com/denmire/JenkinsDependencyCheckTest.git', branch: 'master'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML -n --nvdApiKey 3dbd2f8f-ec1b-4265-aaa7-d5faacb825eb', odcInstallation: 'OWASP Dependency Check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}