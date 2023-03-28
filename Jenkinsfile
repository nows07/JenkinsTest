pipeline  {
	agent any
	environment {
		dockerHome = tool 'nowsDocker'
		mavenHome = tool 'nowsMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
    stage('Compile') {
		steps {
			sh 'mvn clean compile'
			echo "compile done"
		}
		
	}
	stage('Test') {
		steps {
			sh 'mvn test'
			echo "Test"
		}
		
	}
	stage('Integration Test') {
		steps{
			sh 'mvn test'
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
