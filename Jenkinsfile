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
                    rm -rf node_modules
                    npm ci
                    npm run build
                    ls -lah
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:22-bookworm'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Test stage"
                    CI=true npm test
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