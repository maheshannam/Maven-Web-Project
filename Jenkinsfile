#!groovy

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '3'))])

// numToKeepStr: '3' --> It will keep the number of builds

node {
     
  stage('Checkout'){
          checkout scm
       }

       stage('BuildArtifact'){
          def mvn_version = 'M2_HOME'
          withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
          sh "mvn clean package"
       // bat "mvn clean package"       
          }
       }
  
      /*stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }*/
       
}
