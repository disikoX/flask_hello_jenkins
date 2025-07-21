pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent-my-app'
            defaultContainer 'python'
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    component: ci
spec:
  containers:
    - name: python
      image: python:3.7
      command:
        - cat
      tty: true
      volumeMounts:
        - name: workspace-volume
          mountPath: /home/jenkins/agent
  volumes:
    - name: workspace-volume
      emptyDir: {}
"""
        }
    }

    stages {
        stage('Test python') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'python test.py'
            }
        }
    }
}

