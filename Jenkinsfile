pipeline{
  agent { label 'any'}
  options {
    buildDiscarder(logRotator(numToKeepStr:'5'))
  }
  environment{
    DOCKERHUB_CREDENTIALS = credentials('durga123679-dockerhub')
  }
  stages{
    stage('Build'){
      steps {
        sh 'docker build -t durga123679/dp-apline:latest .'
      }
    }
    stage('Login'){
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('PUSH')
    {
      steps{
        sh 'docker push durga123679/dp-alpine:latest'
      }
    }
  }
  post{
    always {
      sh 'docker logout'
    }
  }
}
