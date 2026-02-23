pipeline {
    agent any

    tools {
        jdk 'JDK21'           // Must match Jenkins JDK config
        maven 'Maven3'        // Must match Jenkins Maven config
    }

    stages {

        stage('Clone Code') {
            steps {
                git url: 'https://github.com/The-Puneet-Kumar/jenkins-maven-app.git'
            }
        }

        stage('Clean & Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '🎉 Build successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
