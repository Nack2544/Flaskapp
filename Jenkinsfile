pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/Nack2544/Flaskapp.git', branch: 'main')
      }
    }

    stage('Docker login') {
      steps {
        sh 'docker login -u nack2529 -p dckr_pat_E6B0GlwBxSXQ5zqMhkHobitCzCk'
      }
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t nack2529/flask_app .'
      }
    }

    stage('Docker Push') {
      steps {
        sh 'docker push nack2529/flask_app'
      }
    }

  }
}