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
                //sh 'mkdir -p release'
            }
            // post { 
            //     always {
            //         echo 'Archiving artifacts'
            //         archiveArtifacts artifacts: 'release/', onlyIfSuccessful: true                     
            //     }
            // }
        }
        stage('Tag Repo') {
            steps {
                environment {
                    GIT_CREDENTIALS = credentials('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') // Assuming you have stored your PAT in Jenkins credentials with ID 'github-token'
                }
                script {
                    def buildNumber = env.BUILD_NUMBER
                    sh 'git config --global user.email "suchitrakadolkar2654@gmail.com"'
                    sh 'git config --global user.name "SuchitraKadolkar"'
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
