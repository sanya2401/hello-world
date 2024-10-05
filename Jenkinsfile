pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Example: Use Maven for building
                // sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Example: Run unit tests with a test tool like JUnit
                // sh 'mvn test'
            }
            post {
                always {
                    emailext(
                        to: 'karanbalhotra@example.com',
                        subject: "Unit and Integration Tests: ${currentBuild.currentResult}",
                        body: "The Unit and Integration tests have finished with status: ${currentBuild.currentResult}. Check the attached logs for details.",
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Example: Use SonarQube for static code analysis
                // sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Example: Use a security tool like OWASP Dependency Check
                // sh 'dependency-check.sh --project myApp'
            }
            post {
                always {
                    emailext(
                        to: 'karanbalhotra@example.com',
                        subject: "Security Scan Completed: ${currentBuild.currentResult}",
                        body: "The security scan has finished with status: ${currentBuild.currentResult}. Logs are attached for your reference.",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Example: Deploy to AWS EC2 or other environments
                // sh 'deploy.sh staging'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Example: Run tests on the staging environment
                // sh 'mvn verify -Pstaging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Example: Deploy to AWS EC2 or production server
                // sh 'deploy.sh production'
            }
        }
    }

    post {
        success {
            emailext(
                to: 'karanbalhotra@example.com',
                subject: "Jenkins Pipeline Success",
                body: "The pipeline completed successfully. Well done!",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: 'karanbalhotra@example.com',
                subject: "Jenkins Pipeline Failure",
                body: "The pipeline failed. Check the logs for details.",
                attachLog: true
            )
        }
    }
}
