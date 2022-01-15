pipeline {
	environement {
	  registry = "ayoub12022001/tpdevops"
	  registryCredentials = "dockerhub"
	  dockerImage = ""
	}
	
	agent any
	
	stages {
	  stage ('Build') {
	           steps {
	                  sh "mvn package"
	                 }
	
		}
		
	 stage ('Building Image') {
	  	steps {
	          script {
		         dockerImage = docker.build registry + ":$BUILD_NUMBER"
	             }
	
	         }
	
	    }
	    
	     stage ('Deploy Image') {
	  	steps {
	          script {
		         docker.withRegistry('', registryCredential){
		           dockerImage.push()
		          }
	             }
	
	         }
	
	    }
	    
	 
	
	}	
}
	
