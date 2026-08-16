pipeline {
    agent {
        docker {
            image 'node:18-alpine'
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Build Image') {
            agent none
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