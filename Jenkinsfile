pipeline {
    agent any

    tools {
        jdk 'jdk-17'
        maven 'maven-3.9.4'
    }

    environment {
        MAVEN_OPTS = "-Dmaven.test.failure.ignore=false"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/XJ-NCS/practice.git'
            }
        }

        stage('Build') {
            steps {
                dir('my-app'){
                    bat 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('my-app'){
                    bat 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('my-app'){
                    bat 'mvn package'
                }
            }
        }
    }

    post {g
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build failed. Check logs for details.'
        }
    }
}
