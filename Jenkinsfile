pipeline {
    agent any
    
    stages {
        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Maven build successful'
                }
                failure {
                    echo 'Maven build failed'
                }
            }
        }
    }
}
