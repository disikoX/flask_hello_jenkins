pipeline {
    agent {
        kubernetes {
            inheritFrom 'default'
            containerTemplate {
                name 'python'
                image 'python:3.7'
                command 'cat'
                ttyEnabled true
            }
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
