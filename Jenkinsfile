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
                bat 'docker ps -q --filter "name=cicd-container" | findstr . && docker stop cicd-container'
                bat 'docker ps -a -q --filter "name=cicd-container" | findstr . && docker rm cicd-container'
                bat 'docker run -d -p 8080:80 --name cicd-container devops-cicd-project'
            }
        }
    }
}
