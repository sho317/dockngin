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
    	agent any
      steps {
      	sh 'docker build -t sho317/docknginix:${BUILD_NUMBER} .'
      }
    }
  }
}
