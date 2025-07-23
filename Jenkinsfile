pipeline {
    agent {
        kubernetes {
            inheritFrom 'default'
            label 'my-python-job'
            containerTemplate {
                name 'python'
                image 'python:3.7'
                command 'cat'
                ttyEnabled true
            }
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
  - name: jnlp
    image: jenkins/inbound-agent:4.11-1
"""
        }
    }
    stages {
        stage('Test python') {
            steps {
                container('python') {
                    sh "pip install -r requirements.txt"
                    sh "python test.py"
                }
            }
        }
    }
}
