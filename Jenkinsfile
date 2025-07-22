pipeline {
    agent any

    stages {
        stage('Test python') {
            steps {
                sh 'python3 -m venv venv'
                sh 'pip install -r requirements.txt'
                sh 'python test.py'
        }
    }
 }
}


