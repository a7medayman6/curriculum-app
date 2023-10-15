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
        DOCKERHUB_CREDS = 'credentials(\'dockerhub-creds\')'
      }
      steps {
        sh '''echo docker login -u "${DOCKERHUB_CREDS_USR}" -p "${DOCKERHUB_CREDS_PSW}"

docker login -u ${DOCKERHUB_CREDS_USR} -p ${DOCKERHUB_CREDS_PSW}'''
        sh 'docker login -u $DOCKERHUB_CREDS_USR -p $DOCKERHUB_CREDS_PSW'
      }
    }

  }
  environment {
    DOCKERHUB_CREDS = 'credentials(\'dockerhub-creds\')'
  }
}