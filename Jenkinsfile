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
                'echo Testing'
            }
        }
        stage ('Deploy') {
            steps {
             'echo Deploy'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'It was completed perfectly'
        }
        failure {
            echo 'It failed.  Sorry'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'for example, if the Pipeline was previously failing but is now successful'
        }
    }
    
}