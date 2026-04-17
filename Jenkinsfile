pipeline {
    agent any

    stages {
        stage('w/ docker') {
            agent {
                docker {
                    image 'node:18-alpine'
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