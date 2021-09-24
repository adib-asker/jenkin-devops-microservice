//SCRIPTED
//declarative pipe line
pipeline {
	//agent any
	agent { docker { image 'maven:3.6.3'} }
	stages{
		stage('Build'){
			steps{

				sh 'mvn --version'
				echo "Build"
				

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
