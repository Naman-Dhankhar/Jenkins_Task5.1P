pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'https://github.com/Naman-Dhankhar/Jenkins_Task5.1P.git'
        TESTING_ENVIRONMENT = 'TestEnv'
        PRODUCTION_ENVIRONMENT = 'Naman'
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path: ${env.DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artifacts"
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }

        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application to testing environment: ${env.TESTING_ENVIRONMENT}"
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
