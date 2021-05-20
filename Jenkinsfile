node {
  env.NEW_VERSION = '1.0.0'
  
  stage('build') {
    echo 'building the application'
    echo "build version ${NEW_VERSION}"
    bat 'javac Hello.java'
    bat 'java Hello'
  }
    
  stage('test') {
    echo 'testing the application'
  }

  stage('deploy') {
    echo 'deploying the application'
    withCredentials([usernamePassword(credentialsId: 'server-credentials', usernameVariable: 'USER', passwordVariable: 'PWD')]) {
      echo "user: ${USER}, pwd: ${PWD}"
    }
  }
}
