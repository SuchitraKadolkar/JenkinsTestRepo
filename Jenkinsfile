pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Example build steps
                    sh 'mkdir -p output'
                    sh 'echo "Build artifact content" > output/artifact.txt'
                }
            }
        }
        stage('Archive') {
            steps {
                // Archive artifacts with a custom name or structure
                archiveArtifacts artifacts: 'output/*', allowEmptyArchive: true
            }
        }
    }
}

