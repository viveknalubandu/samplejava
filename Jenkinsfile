pipeline {
 agent none
 tools {
    	maven 'Maven'
 }
 stages {
  stage("Junit"){
   agent any
   steps{
     checkout scm
     //sh 'mvn clean test'
   }
  }
  
  stage("Tests") {
   agent any
   steps {
    checkout scm
    sh 'mvn clean test'
    step([$class: 'Publisher', reportFilenamePattern: '**/testng-results.xml'])
   }
  }
  stage('Deploy'){
   agent any
   steps{
     snDevOpsChange()
   }
  }
 }
}
