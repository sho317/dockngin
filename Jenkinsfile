#!groovy

pipeline {
	agent any
	environment {
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
  stages {
      stage('Checkout'){
          steps {
              git branch: 'main', 
              credentialsId: '30827c1f-150e-46eb-9918-0607886a3c9d',
              url: 'https://github.com/sho317/dockngin'
          }
      }
      stage('Docker Build') {
      steps {
      	sh 'docker build -t sho317/docknginix:${BUILD_NUMBER} .'
      }
    }
	stage('DockerImg Push'){
		steps{
			withDockerRegistry(credentialsId: '90560b0f-8543-4efc-9f73-b06cad14c5d0', url: 'https://index.docker.io/v2') {
    sh 'docker push sho317/docknginix:latest'
}
  }
}
  }}
