pipeline {
	agent any
	tools {
        maven 'maven-3.6.3' 
        }
	environment {
		version = "${BUILD_NUMBER}"
		project = 'clx-repx'
		image = "$project:$version"
	}	
	stages {

    stage('Build Docker Image'){
     steps {	
     		echo "Current Build Number is : ${BUILD_NUMBER}"
     		echo "Current Build Number is : ${version}"
     		echo "Current Image Name is : ${image}"

 			bat 'docker build -t ${image} .'
		}
   }
   
}
}
