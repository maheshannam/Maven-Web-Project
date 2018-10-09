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
       sh 'Jenkins.instance.getItemByFullName('JobName').builds.findAll { it.number > $BUILD_NUMBER && it.number < $BUILD_NUMBER-5 }.each { it.delete() }'
	       }
       }
	   
      /*stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }*/
       
}
