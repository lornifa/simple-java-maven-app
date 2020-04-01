pipeline {

	agent any
	
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
		
		stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
		
		  stage('Deliver') { 
            steps {
				bat 'cd ..'
				bat 'echo test'
				bat 'cd jenkins'
				bat 'cd scripts'
                bat './jenkins/scripts/deliver.bat'' 
            }
        }
    }
	
	
}
