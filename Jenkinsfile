pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Abdul007-tech/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Code Analysis') {
            steps {
                sh 'echo "Running ESLint..." && npm run lint || true'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                sh 'npm run coverage || true'
            }
        }

        stage('NPM Audit (Security Scan') {
            steps {
                sh 'npm audit || true'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Staging simulation: App would be deployed here.'
                sh 'echo "Simulating deployment" && sleep 3'
            }
        }

        stage('Integration Test on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
                sh 'echo "Simulating integration tests on staging server (e.g., Postman or Cypress)"'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production (simulated)...'
                sh 'echo "Simulating deployment to production server (e.g., AWS EC2 or Heroku)"'
            }
        }
    }

    post {
    success {
        emailext(
            subject: 'Jenkins Build Success - 8.2CDevSecOps',
            body: """
            The pipeline build completed successfully.

            Project: 8.2CDevSecOps
            Build: ${env.BUILD_URL}
            """,
            to: 'abdulrehmanraja007@gmail.com',
            attachLog: true
        )
    }

    failure {
        emailext(
            subject: 'Jenkins Build Failed - 8.2CDevSecOps',
            body: """
            The pipeline failed.

            Project: 8.2CDevSecOps
            Build: ${env.BUILD_URL}

            Check attached log for more details.
            """,
            to: 'abdulrehmanraja007@gmail.com',
            attachLog: true
        )
    }

    always {
        echo 'Cleaning up workspace...'
        cleanWs()
    }
}


        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
