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
			withDockerRegistry(credentialsId: '2b0a9e31-d25f-4d7e-aa3d-04fb7fcb6014', url: 'https://hub.docker.com/repository/docker/sho317/docknginix') {
    sh 'docker push sho317/docknginix:${BUILD_NUMBER}'
}
  }
}
  }}
