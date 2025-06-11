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

        stage('Package') {
            steps {
                dir('my-app'){
                    bat 'mvn package'
                }
            }
        }

        stage('Run') {
            steps {
                dir('my-app'){
                    bat 'java -cp target/my-app-1.0-SNAPSHOT.jar com.example.App'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build failed. Check logs for details.'
        }
    }
}
