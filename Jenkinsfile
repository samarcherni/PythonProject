pipeline {
  agent any
  environment {
       DOCKERHUB_USERNAME = "samarcherni"
       
  }

  stages {
    stage('GIT Checkout') {
      steps {
        git branch: 'main',
          url :'https://github.com/samarcherni/PythonProject.git'
      }
    }

  }
}