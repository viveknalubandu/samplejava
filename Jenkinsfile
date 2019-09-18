pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
                steps {
                    snDevOpsStep 'e117e31cdb448050bc8cdd384b96198c'
                     echo "Building" 
                      sh 'mvn -X clean install -DskipTests'
                     sleep 5
                }
       }
       stage("test") {
           steps {
               snDevOpsStep '6117e31cdb448050bc8cdd384b96198c'
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
               snDevOpsStep 'e917e31cdb448050bc8cdd384b96198b'
               snDevOpsChange()
               echo "Deploying"
               // release process
              
               sleep 7
           }
       }
   }
}
