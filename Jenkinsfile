//SCRIPTED
//declarative pipe line
pipeline {
	agent any
	tools {
		maven 'myMaven'
		dockerTool 'myDocker'
	}
	//agent { docker { image 'maven:3.6.3'}}
	environment {

		dockerHome = 'myDocker'
		mavenHome = 'myMaven'
		PATH="/dockerHome/bin:mavenHome:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG -$env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				
			}
		}
		stage('Compile'){
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps {
				
				sh "mvn test"
				

			}
		}
		stage('Integration Test'){
			steps {
				
				sh "mvn failsafe:integration-test failsafe:verify"

			}
		}
		stage('Package'){
			steps {
				
				sh "mvn package -DskipTests"

			}
		}
		stage('Build Docker Image'){
			steps{
				//"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
				script {
				  dockerImage =	docker.build("in28min/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}

		}
		stage('Push Docker Image'){
			steps{
				script{
					
					docker.withRegistry('', 'dockerhub') {
					docker.build("amiadib123/currency-exchange-devops:${env.BUILD_TAG}").push();
					docker.build("amiadib123/currency-exchange-devops:${env.BUILD_TAG}").push('latest');
				}
			}
			}
		}
	} 
	
	post {
		always{
			echo'I am awesome. i run always'
		}
		success{
			echo 'I run when when you success'
		}
		failure{
			echo 'I run when you fail'
		}
		//changed
	}
	
	
}
