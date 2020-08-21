pipeline {
	agent any
	tools {
        maven 'maven-3.6.3' 
        }
		
	stages {

    stage('Build Docker Image'){
     steps {		
			bat 'docker build -t clx-repx:1.0.${env.BUILD_ID} .'
		}
   }
   
     stage('Push NGINX Docker Image'){
		steps {
        	echo 'connecting to ECR.. '
           withDockerRegistry([url: "https://310643530327.dkr.ecr.us-west-2.amazonaws.com/nginx",credentialsId: "ecr:us-west-2:aws-credentials"]) {
           bat 'docker tag clx-repx:1.0.${env.BUILD_ID} 310643530327.dkr.ecr.us-west-2.amazonaws.com/clx-repx:1.0.${env.BUILD_ID}'
	   bat 'docker push 310643530327.dkr.ecr.us-west-2.amazonaws.com/clx-repx:1.0.${env.BUILD_ID}'
               }
	    }
	}

}
}
