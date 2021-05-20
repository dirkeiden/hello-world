pipeline {
  
  agent any
  
  environment {
    NEW_VERSION = '1.0.0'
  }
  
  stages {
    stage("build") {
      steps {
        echo 'building the application'
        echo "build version ${NEW_VERSION}"
        bat 'javac Hello.java'
        bat 'java Hello'
      }
    }
    
    stage("test") {
      steps {
        echo 'testing the application'
      }
    }

    stage("deploy") {
      steps {
        echo 'deploying the application'
        withCredentials([
          usernamePassword(credentialsId: 'server-credentials', usernameVariable: 'USER', passwordVariable: 'PWD')
        ]) {
          echo "user: ${USER}, pwd: ${PWD}"
        }
      }
    }
  }
}
