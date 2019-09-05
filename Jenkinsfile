pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
                steps {
                    snDevOpsStep '76f24192db23ff00bffe5223dc96195a'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
                }
       }
       stage("test") {
           steps {
               snDevOpsStep 'f2f24192db23ff00bffe5223dc96195a'
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
               snDevOpsStep 'faf24192db23ff00bffe5223dc961959'
               snDevOpsChange(ignoreFailure:true)
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
