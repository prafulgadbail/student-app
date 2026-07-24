pipeline {
    agent {
        label 'build-agent'
 
    }

    environment {
        ECR_REGISTRY = '261945560801.dkr.ecr.ap-south-1.amazonaws.com'
        BACKEND_IMAGE = '261945560801.dkr.ecr.ap-south-1.amazonaws.com/student-app-backend'
        FRONTEND_IMAGE = '261945560801.dkr.ecr.ap-south-1.amazonaws.com/student-app-frontend'
        AWS_REGION = 'ap-south-1'
        
    }

    stages {
        stage('Build') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
                
            }
        }
        
        stage('Backend Docker Build') {
            steps {
                dir('backend') {
                    sh 'docker build -t ${BACKEND_IMAGE}:${BUILD_NUMBER} .'
                }
            }
        }

        stage('Frontend Docker Build') {
            steps {
                dir('frontend') {
                    sh 'docker build -t ${FRONTEND_IMAGE}:${BUILD_NUMBER} .'
                }
                
            }
        }

        stage('ECR Login') {
            steps {
                sh 'aws ecr get-login-password --region ${AWS_REGION} | docker login --username AWS --password-stdin ${ECR_REGISTRY}'
            }
        }

        stage('ECR Push') {
            steps {
                sh 'docker push ${BACKEND_IMAGE}:${BUILD_NUMBER}'
                sh 'docker push ${FRONTEND_IMAGE}:${BUILD_NUMBER}'
            }
        }

        
    }
}
