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
	agent any
	stages{
		stage('Build'){
			steps{
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
}
