pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/YOUR-USERNAME/YOUR-REPO.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-cicd-project .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name cicd-container devops-cicd-project'
            }
        }
    }
}
