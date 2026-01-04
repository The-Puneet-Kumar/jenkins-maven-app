pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Code already checked out from GitHub'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline SUCCESS ✅'
        }
        failure {
            echo 'CI/CD Pipeline FAILED ❌'
        }
    }
}
