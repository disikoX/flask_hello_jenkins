pipeline {
    agent {
        kubernetes {
            inheritFrom 'default'
            yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: python
    image: python:3.7
    command:
    - cat
    tty: true
"""
        }
    }
    triggers {
        pollSCM('* * * * *')
      }
    stages {
        stage('Test python') {
            steps {
                container('python') {
                    sh "python --version"
                    sh "pip install -r requirements.txt"
                    sh "python test.py"
                }
            }
        }
    }
  stage('Build image') {
    steps {
        container('docker') {
            sh 'docker build -t localhost:3999/pythontest:latest .'
            sh 'docker push localhost:3999/pythontest:latest'
        }
    }
}

}
