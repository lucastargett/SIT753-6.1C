pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using a build automation tool.'
                echo 'Tool: Maven is used to compile and package the code.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit tests to ensure the code functions as expected.'
                echo 'Tool: NUnit for unit tests and Citrus for integration tests.'
            }
            post {
                always {
                    emailext(
                        to: 'lucastargett@gmail.com',
                        subject: 'Jenkins: Unit and Integration Tests Completed',
                        body: '''Stage 2: Unit and Integration Tests have completed. 
                        The status of the stage is: ${currentBuild.currentResult}. 
                        Please find the logs attached.''',
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Analyzing the code to ensure it meets industry standards.'
                echo 'Tool: SonarQube is used for static code analysis.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Performing a security scan to identify vulnerabilities in the code.'
                echo 'Tool: OpenVAS is used for security scanning.'
            }
            post {
                always {
                    emailext(
                        to: 'developer@example.com',
                        subject: 'Jenkins: Security Scan Completed',
                        body: '''Stage 4: Security Scan has completed. 
                        The status of the stage is: ${currentBuild.currentResult}. 
                        Please find the logs attached.''',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying the application to a staging server.'
                echo 'Tool: AWS CLI is used to deploy to an AWS EC2 instance.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests on the staging environment.'
                echo 'Tool: Selenium is used to validate the application in the staging environment.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying the application to a production server.'
                echo 'Tool: Bamboo is used to deploy to the production server.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}