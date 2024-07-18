pipeline {
	agent {
		docker {
			image 'composer:latest'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'composer install'
			}
		}
		stage('Test') {
			steps {
                sh './vendor/bin/phpunit --log-junit logs/unittest.xml tests'
            }
		}
	}
	post {
		always {
			junit testResults: 'logs/unittest.xml'
		}
	}
}
