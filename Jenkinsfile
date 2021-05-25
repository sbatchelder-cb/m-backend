@Library ('cloudbees-shared-libraries') _ 

pipeline {
  agent none
  stages {
    stage ('Example') {
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
          script {
            echoArgs.call 'This is the m-backend repo'
          }
        }
      }
    }
  }
}
