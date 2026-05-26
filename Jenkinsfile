pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                 git 'https://github.com/Aditi7734/ecowaste'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ecocycle-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop ecocycle || true'
                sh 'docker rm ecocycle || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name ecocycle ecocycle-website'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful 🚀 Website is running!'
        }
        failure {
            echo 'Deployment Failed ❌ Check logs'
        }
    }
}
