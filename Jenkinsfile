pipeline {

	agent any
	
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
				archiveArtifacts('target/*.jar')
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
                bat ' cd jenkins && deliver.bat' 
            }
        }
    }
	
	
}
