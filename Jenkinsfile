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
                    sh 'docker run --rm -i hadolint/hadolint < Dockerfile || true'
                }
            }
        }
    stage('Docker build'){
        steps{
            sh 'docker build -t samarcherni/pythonproject:1.0 .'
            }
    }

    stage('Docker Login'){
        steps{
            withCredentials([usernamePassword(credentialsId: '0c6e53ac-b9a2-446f-9858-62607a350606', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
            sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
            }
        }
    }
    stage('Docker push image'){
     steps{
      sh 'docker push samarcherni/pythonproject:1.0'
     }
    }   
        }

  }