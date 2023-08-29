
pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: python
    image: python:alpine3.13
    tty: true
"""
    }
  }
  stages {
    stage ('Build') {
      steps {
        container("python") {
          sh 'python3 ./cicd/build.py'
        }
      }
    }
    stage ('Test') {
      steps {
        container("python") {
          sh 'python3 ./cicd/test.py'
        }
      }
    }
    stage ('Image Push') {
      steps {
        container("python") {
          sh 'python3 ./cicd/imagePush.py'
        }
      }
    }
  }
}
