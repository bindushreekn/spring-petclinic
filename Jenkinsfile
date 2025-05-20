pipeline {
    agent any

    tools {
        jdk 'jdk-17'         // Make sure Jenkins has JDK 17 installed with this name
        maven 'maven-3.8.5'  // Adjust based on the Maven version installed on your Jenkins
    }

    environment {
        MAVEN_OPTS = "-Dmaven.repo.local=.m2/repository"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        always {
            junit '/target/surefire-reports/*.xml'
        }
    }
}
