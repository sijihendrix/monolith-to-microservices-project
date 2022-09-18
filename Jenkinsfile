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
      parallel {
        stage('Tag') {
          steps {
            sh 'docker tag api-user anileloye/api-user'
            sh 'docker tag api-feed anileloye/api-feed'
            sh 'docker tag frontend anileloye/frontend'
            sh 'docker tag reverseproxy anileloye/reverseproxy'
          }
        }

        stage('list images') {
          steps {
            sh 'docker image ls'
          }
        }

      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'anileloye'
        DOCKERHUB_PASSWORD = 'Oluwasijibomi17_'
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