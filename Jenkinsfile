pipeline {
    agent any

    stages {
        stage('w/ docker') {
            agent {
                docker {

                }
            }
            steps {
                sh '''
                    echo "whatever really"
                '''
            }
        }
    }
}