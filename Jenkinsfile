#!groovy

node {
	   
	stage('Checkout'){

          checkout scm
       }

       stage('BuildArtifact'){
         def mvn_version = 'M2_HOME'
         withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
          sh "mvn clean package"
	 }
	       stage('Maintaing builds'){
		       sh 'find $JENKINS_HOME/jobs/$JOB_NAME/builds -type d -perm 0755'
	       }
       }
	   
      /*stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }*/
       
}
