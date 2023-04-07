pipeline {
  agent any  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub_hassan')
  }
    stages {
    stage('Build') {
        steps {
        sh 'sudo docker build -t mlops_task_2:latest .'
        }
    }
    stage('Login') {
        steps {
        sh 'sudo echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        }
    }
    stage('Push') {
        steps {
        sh 'sudo docker tag mlops_task_2:latest hassansaif-0/mlops_task_2:latest'
        sh 'sudo docker push hassansaif-0/mlops_task_2:latest'
        }
    }
    stage('Execute') {
        steps {
            sh 'sudo docker run -d -p 8080:8080/tcp mlops_task_2:latest'
        }
    }
  }
}
