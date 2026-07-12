pipeline {
    agent {
        label 'build-agent'
    }

    stages {
        stage('Build') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }

        }

        stage('Docker Build') {
            steps {
                dir('backend') {
                    sh 'docker build -t student-backend:$(BUILD_NUMBER) .'
                }
            }
        }


    }

}