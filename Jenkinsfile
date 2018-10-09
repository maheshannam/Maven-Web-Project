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
       }
	
	
       stage('BuildArtifact'){
      sh "properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5'))])
"
       }
	
	   
      /*stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }*/
       
}
