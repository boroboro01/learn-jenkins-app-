pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:20.17.0-alpine3.20'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
                echo 'Hello World'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:20.17.0-alpine3.20'
                    reuseNode true
                }
            }
            steps {
                echo 'Test Stage'
                sh '''
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }
}