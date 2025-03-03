pipeline {
    agent any
    triggers {
        cron('H/3 * * * 1')  // This cron expression means "run every 3 minutes on Mondays"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // This runs the Maven build command to build the Spring Petclinic project
                    sh './mvnw clean install -DskipTests' 
                }
            }
        }
        stage('Jacoco Code Coverage') {
            steps {
                script {
                    // This runs the Jacoco plugin to generate a code coverage report
                    sh './mvnw jacoco:report'
                    // Here we archive the code coverage results (optional)
                    junit '**/target/test-classes/org/jacoco/report/*.xml'
                }
            }
        }
    }
    post {
        always {
            // This block runs after the pipeline, for cleanup or logging
            echo 'Pipeline execution completed'
        }
    }
}
