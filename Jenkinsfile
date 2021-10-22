pipeline
{
	agent any
	environment {

   	 PATH = "C:\\WINDOWS\\SYSTEM32"

		}
	tools
	{
		maven 'maven'
	}

	    tools {
	    maven 'MavenTest'
	  }
	options
    {
        // Append time stamp to the console output.
        timestamps()
      
        timeout(time: 1, unit: 'HOURS')
      
        // Do not automatically checkout the SCM on every stage. We stash what
        // we need to save time.
        skipDefaultCheckout()
      
        // Discard old builds after 10 days or 30 builds count.
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
	  
	    //To avoid concurrent builds to avoid multiple checkouts
	    disableConcurrentBuilds()
    }
	stages{
	stage ("checkout")
		{
			steps
			{
				checkout scm
			}
		}
		stage("Maven clean"){
		steps
		{
		  bat  'mvn clean'
		}
		}
	
		stage ('Build')
		{
			steps
			{
				bat 'mvn install'
			}
		}
}
}
