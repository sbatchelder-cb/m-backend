
pipeline {
  agent none
  stages {
    stage ('Build') {
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
      steps {
        container("python") {
          sh 'python3 ./cicd/build.py'
        }
      }
    }
    stage ('Test') {
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
      steps {
        container("python") {
          sh 'python3 ./cicd/test.py'
        }
      }
    }
    stage ('Image Push') {
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
      steps {
        container("python") {
          sh 'python3 ./cicd/imagePush.py'
        }
      }
    }
  }
}
