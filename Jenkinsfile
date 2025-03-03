pipeline {
    agent any

    environment {
        // Define any environment variables here
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Use the 'bat' command to run the build on Windows
                    bat 'mvn clean install'
                }
            }
        }

        stage('Jacoco Code Coverage') {
            steps {
                // This stage is skipped due to earlier failure(s) in the pipeline
                echo 'Jacoco Code Coverage - Skipped'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed'
        }
    }
}
