Jenkinsfile (Declarative Pipeline)
pipeline {
    agent { docker { image 'php' } }
    stages {
        stage('build') {
            steps {
                sh 'php --version'
                sh '''
                    echo "Multiline shell steps works too"
                '''
            }
        }

        stage('Deploy') {
            steps {
                retry(3) {
                    sh 'echo "retry if fails"'
                }

                timeout(time: 3, units: 'MINUTES') {
                    sh 'echo "time out in 3 mins"'
                }
            }
        }

    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
