pipeline {
    agent any

    tools {
        maven 'M2_HOME'
        jdk 'JAVA_HOME'
    }

    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build and test') {
            steps { sh 'mvn -B clean verify' }
        }
        stage('Build Docker image') {
            steps { sh 'docker build -t student-management:${BUILD_NUMBER} .' }
        }
    }

    post {
        always { archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true }
    }
}
