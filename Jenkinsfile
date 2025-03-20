pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'https://github.com/Naman-Dhankhar/Jenkins_Task5.1P.git'
        TESTING_ENVIRONMENT = 'TestEnv'
        PRODUCTION_ENVIRONMENT = 'Naman'
        EMAIL_RECIPIENTS = 'dhankharnaman8841@gmail.com'
    }

    triggers {
        pollSCM('H/2 * * * *') // Polls GitHub every 1 minute
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path: ${env.DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artifacts"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Checking the quality of the code"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Performing security scan"
            }
            post {
                always {
                    emailext subject: "Security Scan Completed",
                        body: "The security scan stage has completed. Please review the logs for details.",
                        to: "${env.EMAIL_RECIPIENTS}"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to staging environment: ${env.TESTING_ENVIRONMENT}"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging environment"
            }
            post {
                always {
                    emailext subject: "Integration Tests Completed",
                        body: "Integration tests on staging have completed. Please review the logs.",
                        to: "${env.EMAIL_RECIPIENTS}"
                }
            }
        }

        stage('Approval') {
            steps {
                echo "Waiting for manual approval..."
                sleep 10
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
