pipeline {
    agent any

    environment {
        GITHUB_REPO = 'https://github.com/Naman-Dhankhar/Jenkins_Task5.1P.git'
        EMAIL = 'dhankharnaman8841@gmail.com'
    }

    triggers {
        pollSCM('H/2 * * * *') // Polls GitHub every 2 minutes
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: "${GITHUB_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }

        stage('Test') {
            steps {
                sh(script: "echo Running tests... ")
            }
            post {
                always {
                    emailext(
                        subject: "Test Stage Result: ${currentBuild.currentResult}",
                        to: "${env.EMAIL}",
                        attachLog: true,
                        body: "Test stage completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                sh(script: "echo Running security scan... ")
            }
            post {
                always {
                    emailext(
                        subject: "Security Scan Stage Result: ${currentBuild.currentResult}",
                        to: "${env.EMAIL}",
                        attachLog: true,
                        body: "Security Scan stage completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
                    )
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Final Stage Result: ${currentBuild.currentResult}",
                to: "${env.EMAIL}",
                attachLog: true,
                body: "The pipeline has completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
            )
        }
    }
}
