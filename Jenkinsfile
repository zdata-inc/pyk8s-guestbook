pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        checkout scm
      }
    }
    stage('build') {
      steps{
        script {
          sh "docker build -t 174863393238.dkr.ecr.us-west-2.amazonaws.com/ci-cd-demo:nginx-latest ./flask-redis"
          sh "docker build -t 174863393238.dkr.ecr.us-west-2.amazonaws.com/ci-cd-demo:nginx-latest ./nginx"
         }
      }
    }
    stage('Push to Registry') {
            steps {
                script {
                    withDockerRegistry([ credentialsId: "ECR", url: "https://174863393238.dkr.ecr.us-west-2.amazonaws.com" ]) {
                     sh "docker push 174863393238.dkr.ecr.us-west-2.amazonaws.com/ci-cd-demo:nginx-latest"
                     sh "docker push 174863393238.dkr.ecr.us-west-2.amazonaws.com/ci-cd-demo:nginx-latest"
                    }
                }
            }
         }

    stage ('test') {
      steps{
        script {
          sh "echo Testing"
        }
      }
    }

    stage ('deploy') {
      steps {
        script {
           withKubeConfig([credentialsId: 'EKS', serverUrl: "https://74A99A33DEC6AE680D631929F926AFAE.sk1.us-west-2.eks.amazonaws.com"]) {
                      sh "kubectl apply -f redis-master-deployment.yaml"
                      sh "kubectl apply -f redis-master-service.yaml"
                      sh "kubectl apply -f redis-slave-deployment.yaml"
                      sh "kubectl apply -f redis-slave-service.yaml"
                      sh "kubectl apply -f frontend-deployment.yaml"
                      sh "kubectl apply -f frontend-service.yaml"
           }
         }
        }
      }
  }
 }
