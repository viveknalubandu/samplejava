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
                   // snDevOpsStep 'ac1715080f6333009d1a986eb4767ee6'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
                 }
             }
          }
       }
       stage("test") {
           steps {
               snDevOpsStep '201715080f6333009d1a986eb4767ee7'
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
               snDevOpsStep '2c1715080f6333009d1a986eb4767ee6'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
