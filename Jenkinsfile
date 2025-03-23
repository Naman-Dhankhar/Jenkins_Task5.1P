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

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the project to staging...'
            }
            post {
                always {
                    emailext(
                        subject: "Deployment to Staging Stage Result: ${currentBuild.currentResult}",
                        to: "${env.EMAIL}",
                        attachLog: true,
                        body: "Deployment to staging stage completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
                    )
                }
            }
        }

        stage('Approval for Production') {
            steps {
                echo 'Fetching approval for production deployment...'
                sleep 10 // Simulating manual approval delay
            }
            post {
                always {
                    emailext(
                        subject: "Approval for Production Stage Result: ${currentBuild.currentResult}",
                        to: "${env.EMAIL}",
                        attachLog: true,
                        body: "Approval for production stage completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
                    )
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the project to production...'
            }
            post {
                always {
                    emailext(
                        subject: "Deployment to Production Stage Result: ${currentBuild.currentResult}",
                        to: "${env.EMAIL}",
                        attachLog: true,
                        body: "Deployment to production stage completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
                    )
                }
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Final Pipeline Result: ${currentBuild.currentResult}",
                to: "${env.EMAIL}",
                attachLog: true,
                body: "The pipeline has completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
            )
        }
    }
}
