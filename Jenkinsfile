pipeline {
    agent any

    environment {
        MAVEN_HOME = tool name: 'Maven 3.6.3', type: 'maven'
        JAVA_HOME = tool name: 'JDK 17', type: 'jdk'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git
                git 'https://github.com/m5651535/PracticeProject.git'
            }
        }
        stage('Build') {
            steps {
                // Use Maven to build the project
                sh "${MAVEN_HOME}/bin/mvn clean install"
            }
        }
        stage('Test') {
            steps {
                // Run unit tests
                sh "${MAVEN_HOME}/bin/mvn test"
            }
        }
        stage('Package') {
            steps {
                // Package the application (for example into a JAR file)
                sh "${MAVEN_HOME}/bin/mvn package"
            }
        }
        stage('Deploy') {
            steps {
                // 這裡你可以加入部署到測試環境或生產環境的腳本
                echo 'Deploying the Java application'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}