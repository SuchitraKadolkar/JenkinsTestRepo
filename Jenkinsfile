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
            post { 
                always {
                    echo 'Archiving artifacts'
                    archiveArtifacts artifacts: 'release/', onlyIfSuccessful: true                     
                }
            }
        }
        stage('Tag Repo') {
            steps {
                script {
                    def buildNumber = env.BUILD_NUMBER
                    sh "git tag -a acds-${buildNumber} -m 'Tagging acds-${buildNumber}'"
                    sh "git push --tags"
                }
            }
        }
        stage('Description') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        currentBuild.description = "Jenkins build"
                    }
                }
            }
        }
    }
}
