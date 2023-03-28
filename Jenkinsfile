pipeline  {
	agent any
	environment {
		dockerHome = tool 'nowsDocker'
		mavenHome = tool 'nowsMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
	stage('Checkout'){
		steps{
			sh 'mvn --version'
			sh 'docker version'
			echo 'build'
			echo 'PATH - $PATH'
			echo 'BUILD_NUMBER - $env.BUILD_NUMBER'
			echo 'BUILD_ID - $env.BUILD_ID'
			echo 'JOB_NAME - $env.JOB_NAME'
			echo 'BUILD_TAG - $env.BUILD_TAG'
			echo 'BUIL_URL - $env.BUIL_URL'
		}
	}
    stage('Compile') {
		steps {
			sh 'mvn clean compile'
			
		}
		
	}
	stage('Test') {
		steps {
			sh 'mvn test'
			
		}
		
	}
	stage('Integration Test') {
		steps{
			sh 'mvn failsafe:integration-test failsafe:verify'
			
		}
		
	}
	stage('package'){
		steps{
			sh "mvn package -DskipTests"
		}

	}
	stage('build docker image'){
		steps{
			//"docker build -t nows07/test-learn:$env.BUILD_TAG"
			script{
				dockerImage = docker.build("nows07/test-learn:${env.BUILD_TAG}")
			}
		}
	}
	stage('Push docker image'){
		steps{
			script{
				docker.withRegistry('','dockerHub'){
					dockerImage = docker.push();
					dockerImage.push('latest');

				}
				
			}
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
