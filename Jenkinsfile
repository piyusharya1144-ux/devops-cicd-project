pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-cicd-project .'
            }
        }
        stage('Run Container') {
            steps {
                bat 'docker stop cicd-container || true'
                bat 'docker rm cicd-container || true'
                bat 'docker run -d -p 8080:80 --name cicd-container devops-cicd-project'
            }
        }
    }
}
