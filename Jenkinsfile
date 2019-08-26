pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
          stages {
             stage("build1") {
                 steps {
                    snDevOpsStep '1b8f45c10f6333009d1a986eb4767e24'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
                 }
             }
          }
       }
       stage("test") {
           steps {
               snDevOpsStep '9b8f45c10f6333009d1a986eb4767e24'
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
               snDevOpsStep '1f8f45c10f6333009d1a986eb4767e24'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
