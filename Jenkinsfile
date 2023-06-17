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
	// agent {docker {image 'maven:3.6.3'}}
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){ // Automatic jenkins behaviour
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "Path - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "Build Id - $env.BUILD_ID"
				echo "Build Tag - $env.BUILD_TAG"
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Intergation Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		// What happens when build fails
	}
	post {
		always{
			echo 'Build finished. Please see result below.'
		}
		success {
			echo 'Build finished successfully!'
		}
		failure {
			echo 'Build failed. Please checkout build logs!'
		}
	}
}