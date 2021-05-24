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
		def mvnHome = tool name: 'maven', type: 'maven'
		withSonarQubeEnv('sonarqube'){
		sh "${mvnHome}/bin/mvn sonar:sonar -Dsonar.projectKey=maven-project2 -Dsonar.host.url=http://13.233.46.41:9000 -Dsonar.login=7f70d9ee734e3be25fd8719d33d9cc206df16060"
	
		}
	}	
        stage("Quality Gate Check Status"){
         	 timeout(time: 1, unit: 'HOURS') {
             		 def qg = waitForQualityGate()
             		 if (qg.status != 'OK') {
                 		 error "Pipeline aborted due to quality gate failure: ${qg.status}"	
			 }
		 }
	 }
	 stage("Deploy to Tomcat"){
			sshagent(['tomcat9-dev']) {
 			 sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@52.66.207.177:/opt/tomcat-9/webapps'
			}
		}
}
