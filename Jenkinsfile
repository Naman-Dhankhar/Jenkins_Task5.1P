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
                echo 'Checking out code from GitHub... (Tool: Git)'
                git branch: 'main', url: "${GITHUB_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project... (Tools: Maven, Gradle, npm, Makefile)'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests... (Tools: JUnit, Selenium, Jest, Mocha, PyTest)'
                sh(script: "echo Running tests... ")
            }
        }

        stage('Code Analysis Check') {
            steps {
                echo 'Running code analysis... (Tools: SonarQube, ESLint, Pylint, Checkstyle)'
                sh(script: "echo Running code analysis... ")
            }
            post {
                always {
                    emailext(
                        subject: "Code Analysis Stage Result: ${currentBuild.currentResult}",
                        to: "${env.EMAIL}",
                        attachLog: true,
                        body: "Code analysis stage completed with status: ${currentBuild.currentResult}.\nConsole log is attached."
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan... (Tools: SonarQube, Snyk, OWASP Dependency Check)'
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
                echo 'Deploying the project to staging... (Tools: Docker, Kubernetes, Helm, Ansible, AWS CodeDeploy)'
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
                echo 'Fetching approval for production deployment... (Manual approval step using Jenkins input or ServiceNow integration)'
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
                echo 'Deploying the project to production... (Tools: Kubernetes, Terraform, AWS CodeDeploy, Jenkins Pipelines)'
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
