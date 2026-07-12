pipeline {
    agent {
        label 'build-agent'
    }

    stages {
        stage('Initialize') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }

        }

        stage('Environment Validation') {
            steps {
                sh 'git --version'
                sh 'java -version'
                sh 'mvn -version'
            }
        }

    }

}