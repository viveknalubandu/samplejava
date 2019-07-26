pipeline {
   agent any
   stages {
       stage("build") {
           steps {
               snDevOpsStep '099ac72a1336bf408b49b2776144b0d0'
               echo "Building"               
               sh 'mvn clean install -DskipTests'
               sleep 5
           }
       }
       stage("test") {
           steps {
               snDevOpsStep '819ac72a1336bf408b49b2776144b0d0'
               echo "Testing"
               sh 'mvn test -Dpublish'
               sleep 3
           }
       }
       stage("deploy") {
           steps {
               snDevOpsStep '899ac72a1336bf408b49b2776144b0d0'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
