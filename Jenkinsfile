pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    bat 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    bat 'mvn test'
                }
            }
        }

        stage('Jacoco Code Coverage') {
            steps {
                script {
                    bat 'mvn jacoco:report'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Customize with your deploy command
                    bat 'deploy-scripts/deploy.bat'
                }
            }
        }
    }

    post {
        success {
            echo 'Build was successful!'
        }
        failure {
            echo 'Build failed.'
        }
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
