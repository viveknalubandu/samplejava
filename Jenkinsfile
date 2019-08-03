pipeline {
    agent any
      tools {
         maven 'Maven'
      }

    stages {
        stage('Build') {
           snDevOpsStep 'c4ac395513c77b0002a9b2776144b0cc'
            steps {
                echo 'Building'
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
           snDevOpsStep '48ac395513c77b0002a9b2776144b0cc'
            stages {
                stage('Building Distributable Package') {
                    steps {
                        echo 'Building'
                    }
                }
                stage('Archiving Package') {
                    steps {
                        echo 'Archiving Aritfacts'
                        archiveArtifacts artifacts: '/*.zip', fingerprint: true
                    }
                }
                stage('Deploying Dev') {
                    steps {
                        echo 'Deploying'
                        timeout(time:3, unit:'DAYS') {
                            input message: "Approve build?"
                        }
                    }
                }
            }

        }
        stage('Deploy to Test') {
           snDevOpsStep 'ff9c395513c77b0002a9b2776144b0cb'
            when {
                branch 'develop' 
            }
            steps {
                echo 'deploying..'
                timeout(time:3, unit:'DAYS') {
                    input message: "Approve build?"
                }
            }
        }
        stage('Deploy to Prod') {
           snDevOpsStep '44ac395513c77b0002a9b2776144b0cc'
            when {
                branch 'release' 
            }
            steps {
                timeout(time:3, unit:'DAYS') {
                    input message: "Deploy to Prod?"
                }
                echo 'Deploying....'
            }
        }
    }
}
