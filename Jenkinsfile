pipeline{
	//agent{docker{ image "node:latest"}}
	agent any
	 tools {
        maven 'myMaven'	
    }
	stages{
		 stage('Checkout') {
            steps {
                checkout scm
                sh 'docker --version'
                sh 'mvn --version'
            }
        }
		
        stage('Build & Unit Tests') {
            steps {
                sh 'mvn  test'
            }
        }

        stage('Integration Tests') {
            steps {
                sh 'mvn  failsafe:integration-test  failsafe:verify'
            }
        }
	}
}