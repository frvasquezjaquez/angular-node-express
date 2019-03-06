pipeline {
    agent any
    environment {
       DEMO = True
    }
    stages {
        stage('Prepare') {
            steps {
                sh "echo Prepare..."

            }
        }
        stage('Build') {
            steps {
                sh "echo Build..."
  
            }
        }
        stage('Test') {
            steps {
                sh "echo Testing..."
            }
        }
        stage('Deploy') {
            sh "echo Testing..."
        }
        stage('Clean') {
            steps {
                sh "echo Testing..."
            }
        }
    }
    post {
        success {
            sh "Success"
        }
    }
}