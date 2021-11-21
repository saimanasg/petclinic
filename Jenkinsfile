pipeline{
   agent any
   
   stages{
	stage('Checkout')
	{
          steps{
	         checkout([
			$class:'GitSCM',
			branches:[[name:'*/master']],
			extensions:[],
			userRemoteConfigs:[[url:'https://github.com/saimanasg/petclinic.git']]
		])
          }
	}
	stage('Build')
	{
	  steps{
		sh 'mvn clean install'
	       }
	  
	}
	
	stage('test')
	{
	  steps{
		sh 'mvn test'
	       }
	  
	}
	
     
	
   }
        post{
                always{
                        junit '/target/surefire-reports/*.xml'
                }
        }
		
	     
}
