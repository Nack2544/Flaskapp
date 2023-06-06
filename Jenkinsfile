pipeline {

      environment {
        registry = "nack2529/flask_app"
        registryCredentialas = "docker"
        cluster_name = "skillstorm"
    }

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
  stage('Build Stage') {
            steps {
                scripts {
                    dockerImage = docker.build(registry)
                }
            }
        }
  }
}