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
  - name: jnlp
    image: jenkins/inbound-agent:4.11-1
    env:
    - name: JENKINS_SECRET
      value: ${JENKINS_SECRET}
    - name: JENKINS_TUNNEL
      value: jenkins-service-name:50000  # Use actual service name
    - name: JENKINS_AGENT_NAME
      value: ${JENKINS_AGENT_NAME}
    - name: JENKINS_URL
      value: http://jenkins-service-name:8080/  # Use actual service name
    - name: JENKINS_AGENT_WORKDIR
      value: /home/jenkins/agent
"""
        }
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
}
