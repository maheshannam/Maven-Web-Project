#!groovy

node {
	   
	stage('Checkout'){

          checkout scm
       }

       stage('BuildArtifact'){
        MAX_BUILDS = 5

for (job in Jenkins.instance.items) {
  println job.name

  def recent = job.builds.limit(MAX_BUILDS)

  for (build in job.builds) {
    if (!recent.contains(build)) {
      println "Preparing to delete: " + build
      // build.delete()
    }
  }
}
       }
	   
      /*stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }*/
       
}
