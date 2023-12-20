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
                    sh 'pip install --upgrade pip'
                    sh 'pip install -r requirements.txt --user'
                }
            }

    stage('Lint Code') {
            steps {
                script {
                    sh 'docker run --rm -v $(pwd):/app -w /app python:latest flake8'
                }
            }
        }
    stage('Docker build'){
        steps{
            sh 'docker build -t samarcherni/pythonproject:1.0 .'
            }
    }
        }

  }