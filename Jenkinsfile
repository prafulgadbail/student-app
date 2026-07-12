pipeline {
    agent {
        label 'build-agent'
    }

    stages {
        stage('Backend Build') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }

        }

        stage('Docker Build') {
            steps {
                dir('backend') {
                    sh 'docker build -t student-backend:${BUILD_NUMBER} .'
                }
            }
        }

        stage('Frontend Build') {
            steps {
                dir('frontend') {
                    sh 'npm ci'
                    sh 'npm run build'
                }
            }
        }


    }

}