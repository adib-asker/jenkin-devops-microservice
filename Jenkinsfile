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
		stage('Build'){
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
		stage('Test'){
			steps{
				
				echo "Test"
				

			}
		}
		stage('Integration Test'){
			steps{
				
				echo "Integration Test"

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
