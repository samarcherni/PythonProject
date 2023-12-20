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
    stage('Install dependencies'){
            steps{
                nodejs('nodeJSInstallationName'){
                    sh 'pip install --upgrade pip'
                    sh 'pip install -r requirements.txt --user'
                }
            }
        }

  }
}