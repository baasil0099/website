pipeline {
    agent any
    stages {
        stage('Job 1: Build') {
            steps {
                sh 'docker build -t abode-app .'
            }
        }
        stage('Job 2: Test') {
            steps {
                sh 'docker run -d --name test-container -p 8081:80 abode-app'
                sh 'sleep 5'
                sh 'docker stop test-container && docker rm test-container'
            }
        }
        stage('Job 3: Prod') {
            when { branch 'master' }
            steps {
                sh 'docker tag abode-app hshar/webapp:prod'
            }
        }
    }
}
