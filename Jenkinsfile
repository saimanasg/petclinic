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
              stage('Deploy')
	{
	  steps{
               //deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://18.219.186.29:8080/')], contextPath: 'note', war: '**/*.war'
               // bat 'scp -i "D:/STUDY/AWS/KeyPairs/mrng.pem" ec2-user@18.191.89.200 target/spring-petclinic-2.5.0-SNAPSHOT.jar ec2-user@18.191.89.200:/home/ec2-user'    
	    sshagent(['deploy_user']) {
					  sh "scp -o StrictHostKeyChecking=no target/petclinic.war ec2-user@3.144.207.66:/home/ec2-user/apache-tomcat-9.0.55/webapps"
                                  }     
      
      
      
      }
	}
	
     
	
   }
       
		
	     
}
