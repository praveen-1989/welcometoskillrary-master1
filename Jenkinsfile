node{
	stage('SCM Checkout'){

		git 'https://github.com/praveen-1989/welcometoskillrary-master1.git'
	}
	stage('Copile-Package'){
		// Get maven home path 
		def mvnHome = tool name: 'maven', type: 'maven'
		sh "${mvnHome}/bin/mvn clean package"
	}
	stage('Jacoco Reports'){

		jacoco deltaBranchCoverage: '10'
	}
	stage('SonarQube Analysis'){ 
		withSonarQubeEnv(credentialsId: 'sona-pipeline') {

		def mvnHome = tool name: 'maven', type: 'maven'

		}
	}	
	
	
}
