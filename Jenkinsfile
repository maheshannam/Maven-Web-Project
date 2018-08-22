#!groovy

node {
    //currentBuild.result = "SUCCESS"

    try {

       stage('Checkout')
       {
          checkout scm
       }
	    
       stage('Sonar') 
       {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
       }

       stage('Deploying to Nexus')
       {
              sh 'mvn clean deploy'
       }
	    
	stage('Checkstyle') 
       {
             sh 'mvn checkstyle:checkstyle'
       }

               stage('PMD') 
	        {
                    sh 'mvn pmd:check'
                }
	    
	    stage('Deploy to Tomcat')
	    {
		    sshagent(['bd4599df-244f-40f8-b453-5464bbc4d04d']) {
                       // some block
                sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.70.133:/opt/apache-tomcat-8.0.53/webapps'
                   }
	    }
      /* stage('mail'){

         mail body: 'project build successful',
                     from: 'devopstrainingblr@gmail.com',
                     replyTo: 'mithunreddytechnologies@gmail.com',
                     subject: 'project build successful',
                     to: 'mithunreddytechnologies@gmail.com'
       }*/
	    
	    

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           /* mail body: "project build error is here: ${env.BUILD_URL}" ,
            from: 'devopstrainingblr@gmail.com',
            replyTo: 'mithunreddytechnologies@gmail.com',
            subject: 'project build failed',
            to: 'mithunreddytechnologies@gmail.com'
            */
        throw err
    }
}


//#!groovy

/*node {
	   
	stage('Checkout'){

          checkout scm
       }

       stage('BuildArtifact'){

          sh 'mvn install'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }
       
}*/
