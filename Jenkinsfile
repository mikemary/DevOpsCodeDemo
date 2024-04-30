
pipeline{
    tools{
       
        maven 'mymaven'
    }
	agent any
      stages{
           stage('Checkout the code'){
	    
               steps{
		 echo 'cloning the repo'
                 git 'https://github.com/Sonal0409/DevOpsClassCodes.git'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'complie the code again..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		  
              steps{
	         
                  sh 'mvn test'
              }
          
          }

	   stage ('Sonar Quality Check'){

		steps{
		  script{
		  withSonarQubeEnv(installationName: 'Sonar-10.5', credentialsId: 'Jenkins-Sonar')
		    sh 'mvn Clean'
		  }
		}
	   }
          stage('Package'){
		  
              steps{
                  sh 'mvn package'
              }
          }
		   
          
      }
}
