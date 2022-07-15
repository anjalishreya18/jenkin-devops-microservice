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
	//agent { docker{ image 'maven:3.6.3'}}
	//agent { docker{ image 'node:13.8'}}
	environment{
		dockerHome= tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH= "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
			sh 'mvn --version'
			sh 'docker version'
			echo "build"
			echo "Path- $PATH"
			echo "BUILD NUMBER- $env.BUILD_NUMBER"
			echo "BUILD ID- $env.BUILD_ID"
			echo "JOB NAME- $env.JOB_NAME"
			echo "BUILD_TAG - $env.BUILD_TAG"
			echo "BUILD_URL- $env.BUILD_URL"
			}
		}
		stage('compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
			//echo "test"
			sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
			//echo "integration test"
			sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image'){
			steps{
				"docker build -t in28min/currency-exchange-devops:env.BUILD_TAG"
				script{
					docker.build(in28min/currency-exchange-devops:${env.BUILD_TAG})
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('','Dockerhub'){
					docker.push();
					docker.push(latest);
				}
			}	
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
