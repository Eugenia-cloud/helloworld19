pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  
  stages {
    stage('build') {
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
        
      }
    }
    stages {
    stage ('Docker') {
  environment {
    registry = "eugenia1/devops-pipeline"
    registryCredential = 'dockerUserID'
  }
}
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
      }
    }
  stage('Test') {
      steps {
        echo "test step"
        sh 'mvn test'
      }
    }
  stage('Deploy') {
      steps {
         script {
        docker.build registry + ":$BUILD_NUMBER"
             }
           }
         }
       }
     }
   } 
 }    
