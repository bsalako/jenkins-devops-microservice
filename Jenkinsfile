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
        stage ('Package') {
            steps {
                sh "mvn package -DskipTests"
            }
        }
        stage ('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build ("bsalako/currency-exchange-devops:${BUILD_TAG}")
                }
            }
        } 
        stage ('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub') {
                        dockerImage.push();
                        dockerImage.push('latest');
                    }
                    
                }
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
