pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:22-bookworm'
                    // This is so that one single workspace is used and shared by the Jenkins agent and
                    // all Docker containers
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -lah
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -lah
                '''
            }
        }
    }

    post {
        cleanup {
            cleanWs()
        }
    }
}