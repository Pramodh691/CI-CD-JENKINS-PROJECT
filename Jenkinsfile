pipeline {
    agent any

    environment {
        DOCKER_PATH = 'C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe'
        IMAGE_NAME  = 'pramodh691/ci-cd-jenkins-project'
        IMAGE_TAG   = 'latest'
    }

    stages {

        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Pramodh691/CI-CD-JENKINS-PROJECT.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage completed'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage completed'
            }
        }

        stage('Docker Build') {
            steps {
                bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" build -t pramo691/ci-cd-jenkins-project:latest ."
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" login -u %DOCKER_USER% -p %DOCKER_PASS%'
                    bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe"push pramo691/ci-cd-jenkins-project:latest,
                }
            }
        }
    }
}
