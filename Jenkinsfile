pipeline {
  agent any  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub_faizan')
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
        sh 'sudo docker tag mlops_task_2:latest faizanulhassan32/mlops_task_2:latest'
        sh 'sudo docker push faizanulhassan32/mlops_task_2:latest'
        }
    }
    stage('Execute') {
        steps {
            sh 'sudo docker run -d -p 8080:8080/tcp mlops_task_2:latest'
        }
    }
  }
}
