pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-cicd-project .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker stop cicd-container || true'
                sh 'docker rm cicd-container || true'
                sh 'docker run -d -p 8080:80 --name cicd-container devops-cicd-project'
            }
        }
    }
}
