def semanticVersion = "${env.BUILD_NUMBER}.0.0-HOTFIX1"
def packageName = "sample_devops-package_${env.BUILD_NUMBER}"
def version = "${env.BUILD_NUMBER}.0"
pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
      
       stage("junit") {
            steps {
               echo "Junit"
               sh 'mvn test'
               sleep 3
               snDevOpsStep()
           }
          post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
          }
       }
      
      stage("testng") {
           steps {
               echo "Testing"
               sh 'mvn test'
               sleep 3
               checkout scm
               sh 'mvn clean test'
               step([$class: 'Publisher', reportFilenamePattern: '**/testng-results.xml'])
           }
        }
    
      stage("deploy") {
             steps{
                  echo "deploy in prod"
                  snDevOpsChange()              
              }
      }  
  }
}
