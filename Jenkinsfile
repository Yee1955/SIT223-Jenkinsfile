pipeline {
    agent any

    environment {
        RECIPIENT = 'alice0312chong@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo '---- Running Build Stage ----'
                echo 'Build the code using Maven to compile and package the application.'
            }
            post {
                success {
                    echo '---- Build Stage Successful ----'
                }
                failure {
                    echo '---- Build Stage Failed ----'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo '---- Running Unit and Integration Tests Stage ----'
                echo 'Run unit tests using JUnit and integration tests using Selenium to ensure proper functionality.'
            }
            post {
                success {
                    echo '---- Unit and Integration Tests Stage Successful ----'
                    script {
                        try {
                            emailext(
                                subject: 'Unit and Integration Tests Stage Success - ${env.JOB_NAME} #${env.BUILD_NUMBER}',
                                body: 'The unit and integration tests stage completed successfully.',
                                to: '${RECIPIENT}',
                                attachLog: true
                            )
                        } catch (Exception e) {
                            echo "Failed to send success email: ${e.getMessage()}"
                        }
                    }
                }
                failure {
                    echo '---- Unit and Integration Tests Stage Failed ----'
                    emailext(
                        subject: 'Unit and Integration Tests Stage Failed - ${env.JOB_NAME} #${env.BUILD_NUMBER}',
                        body: 'The unit and integration tests stage failed. Please check the attached logs for more details.',
                        to: '${RECIPIENT}',
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo '---- Running Code Analysis Stage ----'
                echo 'Integrate SonarQube for code analysis to ensure the code meets industry standards.'
                sleep time: 5, unit: 'SECONDS'
            }
            post {
                success {
                    echo '---- Code Analysis Successful ----'
                }
                failure {
                    echo '---- Code Analysis Failed ----'
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo '---- Running Security Scan Stage ----'
                echo 'Perform a security scan using OWASP ZAP to identify any vulnerabilities in the code.'
            }
            post {
                success {
                    echo '---- Security Scan Successfull ----'
                    emailext(
                        subject: 'Security Scan Success - ${env.JOB_NAME} #${env.BUILD_NUMBER}',
                        body: 'The Security Scan stage completed successfully.',
                        to: '${RECIPIENT}',
                        attachLog: true
                    )
                }
                failure {
                    echo '---- Security Scan Failed ----'
                    emailext(
                        subject: 'Security Scan Failed - ${env.JOB_NAME} #${env.BUILD_NUMBER}',
                        body: 'The Security Scan stage failed. Please check the attached logs for more details.',
                        to: '${RECIPIENT}',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo '---- Running Deploy to Staging Stage ----'
                echo 'Deploy the application to a staging server AWS EC2 instance.'
                sleep time: 5, unit: 'SECONDS'
            }
            post {
                success {
                    echo '---- Deployment to Staging Successful ----'
                }
                failure {
                    echo '---- Deployment to Staging Failed ----'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo '---- Running Integration Tests on Staging Stage ----'
                echo 'Run integration tests on the staging environment using Postman to ensure the application functions as expected in a production-like environment.'
            }
            post {
                success {
                    echo '---- Integration Testing on Staging Stage Successful ----'
                    emailext(
                        subject: 'Integration Tests on Staging Stage Success - ${env.JOB_NAME} #${env.BUILD_NUMBER}',
                        body: 'The integration tests on staging stage completed successfully.',
                        to: '${RECIPIENT}',
                        attachLog: true
                    )
                }
                failure {
                    echo '---- Integration Testing on Staging Failed ----'
                    emailext(
                        subject: 'Integration Tests on Staging Stage Failed - ${env.JOB_NAME} #${env.BUILD_NUMBER}',
                        body: 'The integration tests on staging stage failed. Please check the attached logs for more details.',
                        to: '${RECIPIENT}',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo '---- Running Deploy to Production Stage ----'
                echo 'Deploy the application to a production server AWS EC2 instance.'
            }
            post {
                success {
                    echo '---- Deployment to Production Successful ----'
                }
                failure {
                    echo '---- Deployment to Production Failed ----'
                }
            }
        }
    }
}
