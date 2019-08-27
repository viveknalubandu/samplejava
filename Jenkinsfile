pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
               steps {
                    snDevOpsStep '175ba5590f6333009d1a986eb4767e12'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
               }
       }
       stage("test") {
           steps {
               snDevOpsStep '935ba5590f6333009d1a986eb4767e12'
               echo "Testing"
               sh 'mvn test -Dpublish'
               sleep 3
           }

           post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
            }
       }
       stage("deploy") {
           steps {
               snDevOpsStep '975ba5590f6333009d1a986eb4767e12'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
