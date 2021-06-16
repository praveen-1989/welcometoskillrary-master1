pipeline {
	agent any
	tools {
            maven "MAVEN_HOME"
            jdk "JAVA_HOME"
        }
	environment {
            mvnHome = "/usr/local/apache-maven"
        }
	
	stages {
            stage("clone the SCM") {
                steps {
                    echo 'clone the SCM'
		    git credentialsId: 'githubUsername', url: 'https://github.com/praveen-1989/welcometoskillrary-master1.git'
                }
	    }
	}
	
	stages {
            stage("clean the workspace") {
                steps {
                    echo 'clean the workspace'
		    sh "'${mvnHome}/bin/mvn' clean"
                }
	    }
	}	
}
