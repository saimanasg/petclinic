pipeline{
   agent any
        environment{
                        PATH = "/opt/maven/apache-maven-3.8.4/bin:$PATH"
                        }
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
       
		
	     
}
