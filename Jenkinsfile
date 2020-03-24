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
           snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "sample-devops-webapp.jar","version": "${version}","semanticVersion": "${semanticVersion}","repositoryName": "sample-devops-webapp"}],"stageName": "build"}""")
                    sleep 5
                }
       }
      
      stage("test") {
           steps {
               snDevOpsStep ()
               echo "Testing"
               sh 'mvn test'
               sleep 3
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
      
      stage("post_deploy_test") {
           steps {
               snDevOpsStep ()
               echo " post_deploy Testing"
               sh 'mvn test'
        snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "sample-devops-webapp-art.jar","version": "${version}","semanticVersion": "${semanticVersion}","repositoryName": "sample-devops-webapp-art"}],"stageName": "post_deploy_test"}""")
               sleep 3
           }
          post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
          }
      }
      
      stage("final") {
             steps{
                snDevOpsStep ()
                snDevOpsPackage(name: "sample-devops-webapp-art_${version}", artifactsPayload: """{"artifacts": [{"name": "sample-devops-webapp-art.jar","version": "${version}","semanticVersion": "${semanticVersion}","repositoryName": "sample-devops-webapp-art"}]}""")
                echo "deploy final"
                echo "final deploy in prod"
                snDevOpsChange() 
              }
      }   
      
  }
}
