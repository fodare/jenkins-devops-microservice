// Scripted pipeline approach.

// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test'){
// 		echo "Intergration test"
// 	}
// }

// Scripted pipeline with declearative syntax
// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Intergration test"
// }

// Declearative pipeline
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
		stage('Intergation Test'){
			steps{
				echo "Intergration test"
			}
		}
		// What happens when build fails
	}
	post {
		always{
			echo 'Build finished. Please check build logs.'
		}
		success {
			echo 'Build finished successfully!'
		}
		failure {
			echo 'Build failed. Please checkout build logs!'
		}
	}
}