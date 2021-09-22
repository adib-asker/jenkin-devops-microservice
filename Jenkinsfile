//SCRIPTED
//declarative pipe line
pipeline {
	agent any
	stages{
		stage('Build'){
			steps{
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
	}
	
	
}
