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


    }

}