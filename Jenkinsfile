pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'jenkins-nodejs-app'
    }

    stages {
        stage('Code clone') {
            steps {
                checkout scm
            }
        }
        // stage('Install Dependencies') {
        //     steps {
        //         sh 'npm install'
        //     }
        // }
        // stage('Run Tests') {
        //     steps {
        //         sh 'npm test'
        //     }
        // }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop node-app || true
                docker rm node-app || true
                docker run -d -p 3000:3000 --name node-app $DOCKER_IMAGE
                '''
            }
        }
    }
}