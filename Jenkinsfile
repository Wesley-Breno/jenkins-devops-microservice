pipeline {
	agent any
	// agent any
	// agent { docker { image 'maven:3.6.3'} }
	// agent { docker { image 'node:13.8'} }
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH = $PATH"
				echo "BUILD NUMBER = $env.BUILD_NUMBER"
				echo "BUILD ID = $env.BUILD_ID"
				echo "JOB NAME = $env.JOB_NAME"
				echo "BUILD TAG = $env.BUILD_TAG"
				echo "BUILD URL = $env.BUILD_URL"
			}
		}

		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}

		stage('Test') {
			steps {
				sh "mvm test"
			}
		}
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
	} 
	
	post {
		always {
			echo 'Im awesome, I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}
