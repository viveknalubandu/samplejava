pipeline {
    agent any
      tools {
         maven 'Maven'
      }
    stages {
        stage('Build') {
           
            steps {
                echo 'Building'
                snDevOpsStep 'c4ac395513c77b0002a9b2776144b0cc'
             sh 'mvn clean install'
               sleep 5
            }
         post {
                   always {

                       junit '**/target/surefire-reports/*.xml' 

                   }
               }
        }
        stage('Deploy to Dev') {
            // when {
            //     branch 'develop' 
            // }          
            stages {
                stage('Building Distributable Package') {
                    steps {
                        echo 'Building'
                        snDevOpsStep '48ac395513c77b0002a9b2776144b0cc'
                    }
                }
                stage('Archiving Package') {
                    steps {
                        snDevOpsStep '48ac395513c77b0002a9b2776144b0cc'
                        echo 'Archiving Aritfacts'
                  
                    }
                }
                stage('Deploying Dev') {
                    steps {
                        snDevOpsStep '48ac395513c77b0002a9b2776144b0cc'
                        echo 'Deploying'
                       
                        }
                    }
                }
            }

        }
        stage('Deploy to Test') {          
            steps {
                echo 'deploying..'
                snDevOpsStep 'ff9c395513c77b0002a9b2776144b0cb'
                
            }
        }
        stage('Deploy to Prod') {          
            steps {
                snDevOpsStep '44ac395513c77b0002a9b2776144b0cc'
                echo 'Deploying....'
            }
        }
    }
}
