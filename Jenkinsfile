pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ankandhang/test-case1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t devops-static-site .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    bat 'docker stop static-site || exit 0'
                    bat 'docker rm static-site || exit 0'
                    bat 'docker run -d -p 5000:80 --name static-site devops-static-site'
                }
            }
        }
    }
}
