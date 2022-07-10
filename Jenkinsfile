/*node {
	stage('Build') {
		echo "Build"
	}
	stage('Test') {
		echo "Test"
	}
	stage('Integration Test') {
		echo "Integration Test"
	}
}*/

/*
//scripted
node{
echo "Build"
echo "Test"
echo "Integration Test"
}*/

//DECLARATIVE

pipeline{
	//agent any
	agent { docker{ image 'maven:3.6.3'}}
	stages{
		stage('Build'){
			steps{
			sh "mvn --version"
			echo "build"
			}
		}
		stage('Test'){
			steps{
			echo "test"
			}
		}
		stage('Integration Test'){
			steps{
			echo "integration test"
			}
		}
	}

    post{
		always{
			echo "I am awesome"
		}
		success{
			echo "I run when build success"
		}
		failure{
			echo "I ran when build failure"
		}
	}
}
