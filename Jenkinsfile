pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'python3 Hello.py'
            }
        }
        stage('Test') {
            steps {
                echo "Inside Test pipeline stage."
            }
        }
        stage('Deploy') {
            steps {
                echo "Inside Deploy pipeline stage."
            }
        }
    }
}
