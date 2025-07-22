pipeline {
    agent any

    stages {
          stage('Build Docker Image') {
            steps {
              sh 'docker build -t my-python-app .'
          }
    }  
        stage('Test python') {
            steps {
                sh 'python3 -m venv venv'
                sh 'pip install -r requirements.txt'
                sh 'python test.py'
        }
    }
 }
}


