pipeline {

      environment {
        registry = "Nack2520/flask_app"
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