pipeline {
	agent any
	tools {
        maven 'maven-3.6.3' 
        }
		
	stages {

    stage('Build Docker Image'){
     steps {		
			bat 'docker build -t clx-repx .'
		}
   }
   
     stage('Push NGINX Docker Image'){
		steps {
        	echo 'connecting to ECR.. '
           withDockerRegistry([url: "https://310643530327.dkr.ecr.us-west-2.amazonaws.com/clx-repx",credentialsId: "ecr:us-west-2:aws-credentials"]) {
           bat 'docker tag clx-repx:${BUILD_NUMBER} 310643530327.dkr.ecr.us-west-2.amazonaws.com/clx-repx:${BUILD_NUMBER}'
	   bat 'docker push 310643530327.dkr.ecr.us-west-2.amazonaws.com/clx-repx:${BUILD_NUMBER}'
               }
	    }
	}

}
}
