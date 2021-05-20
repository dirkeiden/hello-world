node {
  env.NEW_VERSION = '1.0.0'
  
  properties([parameters([choice(choices: ['master', 'dev'], description: 'Select branch to build', name: 'branch')])])
  
  stage('checkout') {
    echo "pulling changes from branch ${params.branch}"
    git branch: "${params.branch}", credentialsId: '79de0532-7126-4792-a168-79153cead2b5', url: 'https://github.com/dirkeiden/hello-world.git'
  }
  
  stage('build') {
    echo 'building the application'
    echo "build version ${NEW_VERSION}"
    bat 'javac World.java'
    bat 'java World'
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
