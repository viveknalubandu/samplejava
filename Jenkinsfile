pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
           steps {
              snDevOpsStep '6750e0cc138f770002a9b2776144b046'
               echo "Building" 
                sh 'mvn clean install'
               sleep 5
           }
           post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
            }
          
       }
       stage("test") {
           steps {
               snDevOpsStep '6f50e0cc138f770002a9b2776144b046'
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
               snDevOpsStep 'eb50e0cc138f770002a9b2776144b046'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       
       }
   }
}
