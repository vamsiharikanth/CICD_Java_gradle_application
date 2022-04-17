pipeline{       //jenkins file start with it
    agent any  // specifies on which server our job will run 
    stages{   //
        stage("sonarquality check"){  //sonar quality check stage
            agent {  
                docker {
                    image 'openjdk:11' //for running gradle we need java which we run as docker container
                }
            }
            steps{
                script{
                     withSonarQubeEnv(credentialsId: 'sonar-token') { // from syntax generator in jenkins
                            sh 'chmod +x gradlew' // execute permissions for gradlew script
                            sh './gradlew sonarqube'  // pushes gradlew to sonarqube and execute there
                     }
                      
                }
            }
        }
    }
}
