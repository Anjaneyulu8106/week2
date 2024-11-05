pipeline {
    agent any 

    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/Anjaneyulu8106/week2.git', credentialsId: 'docker-hub-credentials'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    script {
                        // Use bat for Windows
                        bat "echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin"
                    }
                }
            }
        }
        stage('Build') {
            steps {
                bat 'docker build -t my-nodejs-app .'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test commands here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deploy commands here
            }
        }
    }
}
