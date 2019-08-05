pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
          steps {
             snDevOpsStep 'db1cd11d13477b0002a9b2776144b0e2'
               echo "Building" 
                sh 'mvn clean install'
               sleep 5
           }         
       }     

       stage("test") {
           steps {
               snDevOpsStep 'df1cd11d13477b0002a9b2776144b0e2'
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
               snDevOpsStep '5f1cd11d13477b0002a9b2776144b0e2'
               snDevOpsChange()
               echo "Deploying"
              // release process
              sleep 7
           }     
       }

   }

}
