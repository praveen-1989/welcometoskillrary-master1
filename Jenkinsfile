pipeline {
	agent any
	tools {
		maven 'maven'
		jdk 'jdk8'
	}
	
	stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
	
	stages {
		stage (clean workspace){
			echo 'Clean the workspace.'
			sh 'mvn clean'
		}
	}
}
