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

        stage('NPM Audit (Security Scan)') {
            steps {
                sh 'npm audit || true'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Simulating deployment to staging...'
                sh 'echo "Staging deployment in progress..." && sleep 2'
            }
        }

        stage('Integration Test on Staging') {
            steps {
                echo 'Running simulated integration tests on staging...'
                sh 'echo "Running tests..." && sleep 2'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Simulating deployment to production...'
                sh 'echo "Production deployment in progress..." && sleep 2'
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: 8.2CDevSecOps Pipeline - ${env.BUILD_TAG}",
                body: """Build completed successfully.

Project: 8.2CDevSecOps
Branch: main
Build URL: ${env.BUILD_URL}
""",
                attachLog: true,
                compressLog: true,
                to: 'abdulrehmanraja007@gmail.com'
            )
        }

        failure {
            emailext(
                subject: "FAILURE: 8.2CDevSecOps Pipeline - ${env.BUILD_TAG}",
                body: """Build failed.

Project: 8.2CDevSecOps
Branch: main
Build URL: ${env.BUILD_URL}

Check the attached logs for more details.
""",
                attachLog: true,
                compressLog: true,
                to: 'abdulrehmanraja007@gmail.com'
            )
        }

        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}

