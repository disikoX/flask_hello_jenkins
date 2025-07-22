pipeline {
    agent any

    stages {
        stage('Test python') {
            steps {
                container('python') {
                    sh 'pip install -r requirements.txt'
                    sh 'python test.py'
                }
            }
        }
    }
}

