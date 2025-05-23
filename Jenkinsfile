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
                sh 'npm test || true' // Allows pipeline to continue despite test failures
            }
        }
        
        stage('Code Analysis') {
            steps {
                sh 'echo "Running ESLint..." && npm run lint || true'
            } 
        }


        stage('Generate Coverage Report') {
            steps {
                // Ensure coverage report exists
                sh 'npm run coverage || true'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                sh 'npm audit || true' // This will show known CVEs in the output
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Staging simulation: App would be deployed here.'
                sh 'echo "Simulating deployment" && sleep 3' // Just a placeholder for simulation
            }
        }

        stage('Notify') {
            steps {
                echo 'Sending email notification (simulation)...'
                echo 'Subject: Jenkins CI/CD Pipeline Finished'
                echo 'Body: Pipeline completed for Abdul007-tech/8.2CDevSecOps'

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
    

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
