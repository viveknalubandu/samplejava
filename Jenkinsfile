pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
           steps {
              snDevOpsStep 'b21a8b2a1336bf408b49b2776144b0ea'
               echo "Building" 
                sh 'mvn clean install -DskipTests'
               sleep 5
           }
       }
       stage("test") {
           steps {
               snDevOpsStep '632a87ee13f2bf408b49b2776144b0a6'
               echo "Testing"
               sh 'mvn test -Dpublish'
               sleep 3
           }
       }
       stage("deploy") {
           steps {
               snDevOpsStep 'ba3a0f2a1336bf408b49b2776144b0ad'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
