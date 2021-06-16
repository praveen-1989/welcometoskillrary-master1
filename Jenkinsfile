pipeline {
	agent any
	tools {
		maven 'maven'
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
		stage ('Clean Workspace') {
			echo 'Clean the Workspace.'
			sh 'mvn clean'
			}
		}
	}
}
