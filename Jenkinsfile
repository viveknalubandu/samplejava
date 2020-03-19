def semanticVersion = "${env.BUILD_NUMBER}.0.0"
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
                    snDevOpsStep ()
                    echo "Building" 
                    sh 'mvn -X clean install -DskipTests'
                    sleep 5
                }
       }
      stage("test") {
           steps {
               snDevOpsStep ()
               echo "Testing"
               sh 'mvn test'
               sleep 3
              snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "sample-devops-webapp.jar","version": "${version}","semanticVersion": "${semanticVersion}","repositoryName": "sample-devops-webapp"}],"stageName": "test"}""")
           }
          post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
          }
        }
    
      stage("deploy") {
             steps{
                  snDevOpsStep ()
                  echo "deploy in prod"
                  echo "deploy in prod"
                  snDevOpsChange()              
              }
      }   
      stage("final") {
             steps{
                  snDevOpsStep ()
                snDevOpsPackage(name: "sample-devops-webapp_${version}", artifactsPayload: """{"artifacts": [{"name": "sample-devops-webapp.jar","version": "${version}","semanticVersion": "${semanticVersion}","repositoryName": "sample-devops-webapp"}]}""")
                echo "deploy final"
              }
      }   
      
  }
}
