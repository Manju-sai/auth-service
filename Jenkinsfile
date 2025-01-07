pipeline {	
	agent any	
	tools {	    
		maven 'my-maven'		
		jdk 'my-jdk'	
	}	
	stages {        
		stage('Clone'){			
			steps {git url:'https://github.com/Manju-sai/auth-service.git', branch:'main'}			}		
		stage('Build'){			
			steps {sh "clean package -DskipTests"}		
		}		
		stage('PreDeploy'){			
			steps{bat "docker rmi -f auth-img ."			    
			            bat "docker rm -f auth-cntr"	}		
		}
		stage('Deploy') {			
			steps { bat "docker build -t auth-img ."			    
			            bat "docker run -p 6090:8090 -d --name auth-cntr auth-img"}		
		}		
	}
}