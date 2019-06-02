pipeline {
    agent any
    stages{
        stage ('Build') {
            steps{
                sh 'python --version'
                timeout(time: 3, unit: 'MINUTES') {
                    sh 'echo "Hello World"'
                }
                retry(3) {
                    sh '''
                        echo "Multiline shell steps work too"
                        ls -lah
                    '''
                }
             
            }
        }
        stage ('Test') {
            steps {
                sh 'echo "Testing"'
            }
        }
        stage ('Deploy') {
            steps {
                sh 'echo "Deploy"'
            }
        }
    }
    post {
        always {
            sh 'echo "This will always run"'
        }
        success {
            sh 'echo "It was completed perfectly"'
        }
        failure {
            sh 'echo "It failed.  Sorry"'
        }
        unstable {
            sh 'echo "This will run only if the run was marked as unstable"'
        }
        changed {
            sh 'echo "This will run only if the state of the Pipeline has changed"'
            sh 'echo "for example, if the Pipeline was previously failing but is now successful"'
        }
    }
    
}