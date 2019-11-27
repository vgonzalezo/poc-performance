pipeline{
  agent { 
    node {
      label 'nodejs'
    } 
  }
  stages{
    stage ('Checkout codigo fuente'){
      steps{
        checkout scm
      }
    }
    stage ('Desplegar') {
      steps{
        script {
          openshift.withCluster() {
            openshift.withProject() {
              openshift.selector("bc", "performance-report").startBuild("--from-dir=./", "--wait=true", "--follow", "--loglevel=8")
            }
          }
        }
      }
    }

  }
}