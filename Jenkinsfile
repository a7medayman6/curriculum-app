pipeline {
  agent {
    node {
      label 'docker-agent'
    }

  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/faraday-academy/curriculum-app', branch: 'dev')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Test Docker') {
      steps {
        sh '''# docker build -f curriculum-front/Dockerfile -t fuze365/curriculum-front:latest .
docker run hello-world'''
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'fuze365'
        DOCKERHUB_PASSWORD = 'gv1&3Ea9W##onDQAMUG&41CvZ7h1d1'
      }
      steps {
        sh 'docker login -u $dockerhub-creds_USR -p $dockerhub-creds_PSW'
      }
    }

  }
  environment {
    DOCKERHUB_CREDS = 'credentials(\'dockerhub-creds\')'
  }
}