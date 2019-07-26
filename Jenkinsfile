pipeline {
   agent any
   tools {
      maven 'Maven'
   }
   stages {
       stage("build") {
           steps {
              snDevOpsStep 'f44319831336ff408b49b2776144b00a'
               echo "Building" 
                sh 'mvn clean install -DskipTests'
               sleep 5
           }
       }
       stage("test") {
           steps {
               snDevOpsStep '7c4319831336ff408b49b2776144b009'
               echo "Testing"
               sh 'mvn test -Dpublish'
               sleep 3
           }
       }
       stage("deploy") {
           steps {
               snDevOpsStep '784319831336ff408b49b2776144b00a'
               snDevOpsChange()
               echo "Deploying"
               // release process
               sleep 7
           }
       }
   }
}
