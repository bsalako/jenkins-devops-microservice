pipeline { 
    agent any
    stages { 
        stage('Build') {  
            steps { 
                echo "Build"
                echo "Job Name =${JOB_NAME}"
                echo "Build ID =${BUILD_ID}"
                echo "Build URL =${BUILD_URL}"  
            } 
        } 
        stage('Test') {  
            steps { 
                echo "Test"  
            } 
        } 
        stage('Integration Test') {  
            steps { 
                echo "Integration Test"  
            } 
        } 
    } 
	
	post {
		always {
			echo 'I am awesome, I run always'
		}
		success {
			echo 'I run when you are successful'
		}
		failure {
			echo 'I run when you fail'
		}
	}
}
