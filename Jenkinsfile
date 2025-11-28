pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ankandhang/test-case1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t devops-static-site .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop static-site || true'
                    sh 'docker rm static-site || true'
                    sh 'docker run -d -p 5000:80 --name static-site devops-static-site'
                }
            }
        }
    }
}
