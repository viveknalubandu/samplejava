def semanticVersion = "${env.BUILD_NUMBER}.0.0-HOTFIX1"
def packageName = "sample_devops-package_${env.BUILD_NUMBER}"
def version = "${env.BUILD_NUMBER}.0"
pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
      
       stage("build") {
                steps {
                    echo "Building" 
                    sh 'mvn -X clean install -DskipTests'
                    sleep 5
                    snDevOpsStep()
                }
       }
      
      stage("test") {
           steps {
               echo "Testing"
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
    
      stage("deploy") {
             steps{
                  snDevOpsStep()
                  echo "deploy in prod"
                  echo "deploy in prod"
                  snDevOpsChange()              
              }
      }  
  }
}
