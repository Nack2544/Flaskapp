pipeline {

  environment {
    registry = "nack2529/flask_app"
    registryCredentials = "docker"
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
        git(url: 'https://github.com/Nack2544/flasking.git', branch: 'main')
      }
    }

    stage('Build Stage') {
      steps {
        script {
          dockerImage = docker.build(registry)
        }
      }
    }

    stage('Deployment Stage') {
      steps{
        script {
          docker.withRegistry('', registryCredentials) {
            dockerImage.push()
          }
        }
      }
    }
     stage('Kubernetes') {
      steps {
        withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWS', secretKeyVariable: "AWS_SECRET_ACCESS_KEY")]) {
          sh "aws eks --region us-east-1 update-kubeconfig --name ${cluster_name}"
          script {
            try {
              sh "kubectl create nack2529 ${nack2529}"
            }
            catch (Exception e) {
              echo "Error / nack2529 already created"
            }
          }
          sh "kubectl apply -f ./deployment.yaml -n ${nack2529}"
          sh "kubectl -n ${nack2529} rollout restart deployment flaskcontainer"
        }
      }
    }
  }
}