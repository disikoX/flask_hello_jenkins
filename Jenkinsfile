
pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent-my-app'
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
    command: ['cat']
    tty: true
    resources:
      requests:
        cpu: "500m"
        memory: "512Mi"
  - name: jnlp  # Required Jenkins agent container
    image: jenkins/inbound-agent:latest
    args: ['\$(JENKINS_SECRET)', '\$(JENKINS_NAME)']
"""
        }
    }

    stages {
        stage('Test python') {
            steps {
                container('python') {
                    script {
                        sh 'python --version'
                        sh 'pip install -r requirements.txt'
                        sh 'python test.py'
                    }
                }
            }
        }
    }
}
