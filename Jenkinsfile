pipeline {
    agent any

    stages {
      stage('Install Python') {
            steps {
                sh '''
                    sudo apt-get update
                    sudo apt-get install -y python3 python3-pip python3-venv
                '''
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


