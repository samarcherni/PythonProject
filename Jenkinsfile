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

    stage('Lint Dockerfile') {
            steps {
                script {
                    // sh 'docker build -t dockerfile-linter -f Dockerfile.lint .'
                    // sh 'docker run --rm dockerfile-linter sh -c "hadolint --fail-level warning /Dockerfile"'
                    sh 'docker run --rm -i hadolint/hadolint - < Dockerfile || true'
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