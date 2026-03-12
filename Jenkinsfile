pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "2023bcs0097irine/2023bcs0097irine-2023bcs0097_2023bcs0097"
        DOCKER_CREDS_ID = "dockerhub-credentials"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Login DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials',
                usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'docker login -u $USER -p $PASS'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

    }
}
