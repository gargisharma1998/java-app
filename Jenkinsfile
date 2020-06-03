pipeline {
   agent any

   stages {
      stage('Docker build') {
         steps {
           sh 'docker build -t gargisharma20/springjava:complete'.
         }
      }
      stage('Push image to Dockerhub') {
         steps {
            sh 'docker push gargisharma20/springjava:complete'
         }
      }
      stage('deploy container on minkube cluster')
         steps {
            sh 'kubectl apply -f deploy.yml'
         }
      stage('Service creation') {
          steps {
              sh 'kubectl apply -f service.yml'
          }
      }
      stage('Ingress creation') {
          steps {
              sh 'kubectl apply -f ingress.yml'
              sleep 60
              sh 'minikube service java-app --url'
          }
          }
      }
      
   }


