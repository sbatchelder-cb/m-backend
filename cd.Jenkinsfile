
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
    stage ('Deploy') {
      steps {
        container("python") {
          sh 'python3 ./cicd/deploy.py'
        }
      }
    }
  }
}
