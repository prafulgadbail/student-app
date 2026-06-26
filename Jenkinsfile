pipeline {

    agent {
        label 'build-agent'
    }

    stages {

        stage('Agent Test') {
            steps {
                sh 'hostname'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Build started"
            }
        }

        stage('Test') {
            steps {
                echo "Testing application"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application"
            }
        }

    }

    post {

        success {
            echo "Pipeline Success"
        }

        failure {
            echo "Pipeline Failed"
        }

    }
}
