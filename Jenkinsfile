pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
                steps {
                    snDevOpsStep '373b11150f6333009d1a986eb4767e06'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
                }
       }
       stage("test") {
           steps {
               snDevOpsStep 'b73b11150f6333009d1a986eb4767e06'
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
               snDevOpsStep 'b33b11150f6333009d1a986eb4767e06'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
