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
                    snDevOpsStep 'ee2f81c10f6333009d1a986eb4767e3a'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
                 }
             }
          }
       }
       stage("test") {
           steps {
               snDevOpsStep '622f81c10f6333009d1a986eb4767e3b'
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
               snDevOpsStep 'e62f81c10f6333009d1a986eb4767e3a'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
