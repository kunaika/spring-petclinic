pipeline {
    agent any

    triggers {
        cron('H */3 * * 1')  // Trigger every 3 minutes on Mondays
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Compile and build the artifact
                    sh './mvnw clean package -DskipTests'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Run tests and generate Jacoco code coverage report
                    sh './mvnw jacoco:report'
                }
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }
}
