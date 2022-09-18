pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/sijihendrix/monolith-to-microservices-project.git', branch: 'deployment')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker-compose -f docker-compose.yaml build'
      }
    }

    stage('Tag') {
      steps {
        sh 'docker tag api-user anileloye/api-user:latest'
        sh 'docker tag api-feed anileloye/api-feed:latest'
        sh 'docker tag frontend anileloye/frontend:latest'
        sh 'docker tag reverseproxy anileloye/reverseproxy:latest'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'anileloye'
        DOCKERHUB_PASSWORD = 'gv1&3Ea9W##onDQAMUG&41CvZ7h1d1'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push anileloye/frontend'
        sh 'docker push anileloye/api-user'
        sh 'docker push anileloye/api-feed'
        sh 'docker push anileloye/reverseproxy'
      }
    }

  }
}