pipeline  {
	agent { docker { image 'maven:3.6.3' } }
	stages {
    stage('Build') {
		steps {
			sh 'mvn --version'
			echo "Build"
		}
		
	}
	stage('Test') {
		steps {
			echo "Test"
		}
		
	}
	stage('Integration Test') {
		steps{
			echo "Integration Test"
		}
		
	}
	}
	post {
		always {
			echo "Im awesome always!"
		}
		success {
			echo "Im awesome success!"
		}
		failure {
			echo "Im awesome failure!"
		}
	}
	
}
