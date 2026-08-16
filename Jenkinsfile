pipeline {
    agent none
    stages {
        stage('Install Dependencies') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'npm test'
            }
        }
        stage('Build Image') {
            agent any
            steps {
                sh 'docker build -t my-app:${BUILD_NUMBER} .'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished processing.'
        }
    }
}