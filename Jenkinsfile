pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
                steps {
                    snDevOpsStep 'f5a48af91373ff0002a9b2776144b00e'
                     echo "Building" 
                      sh 'mvn clean install -DskipTests'
                     sleep 5
                }
       }
       stage("test") {
           steps {
               snDevOpsStep 'f9a48af91373ff0002a9b2776144b00e'
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
               snDevOpsStep '79a48af91373ff0002a9b2776144b00e'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
