node{
	stage('SCM Checkout'){

		git 'https://github.com/praveen-1989/devops1.git'
	}
	stage('Copile-Package'){
		// Get maven home path 
		def mvnHome = tool name: 'maven-3', type: 'maven'
		sh "${mvnHome}/bin/mvn clean package"
	}
	stage('SonarQube Analysis'){ 
		def mvnHome = tool name: 'maven-3', type: 'maven'
		withSonarQubeEnv('sonarqube'){
		sh "${mvnHome}/bin/mvn sonar:sonar"
		}
	}
	
	stage('Quality Gate Status'){
		timeout(time: 1, unit: 'HOURS'){
			def qg = waitForQualityGate()
			if (qg.status != 'ok') {
				error "Pipeline aborted due to quality gate failure: ${qg.status}"
		sh "${mvnHome}/bin/mvn sonar:sonar"
		              }
	            }
	        }
}
