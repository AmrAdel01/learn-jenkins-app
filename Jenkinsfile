pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
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
                echo "== Build output =="
                ls -R
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'test -f dist/index.html'
            }
        }
    }
}
