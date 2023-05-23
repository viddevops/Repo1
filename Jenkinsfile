pipeline {
    agent any
    stages { stage('Initiation') 
	//start of the parallel block
	       { parallel   {
						stage ('Introduction')
						{steps 
						{bat 'echo "Hello, This is my first pipeline project"'}}
						stage('Environment variables') 
						{steps 
						{bat 'set "JAVA_HOME"'
						 bat 'set "MAVEN_HOME"'}
						}
						} 
						}	
	//end of the parallel block		

    //start of the sequential stages	
		stage('Maven clean, compile') 
		{steps 
		{bat 'mvn -version'
		 bat 'mvn clean compile'}
		}
						
		stage('Maven install, deploy') 
		{steps {bat 'mvn install deploy'}}
            }
	//end of the sequential stages

    //start of the post action block	
		post {
		//always { bat 'echo "The job is complete"'}
		//{build 'maven_job1'}}
		//{emailext attachLog: true, body: 'Please find the status of the job in the attached log', subject: 'JOB Status email', to: 'ramkumar.kumaresan@gmail.com'}
        success { bat 'echo "The job is successful"'}
		unstable { bat 'echo " The job is unstable"'}
		failure { bat 'echo "The job is failed"'}
		     }
    //end of the post action block			 
		  }