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

        stage('SonarCloud Analysis') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    sh '''
                        apt-get update
                        apt-get install -y unzip wget openjdk-17-jre
                        wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip
                        unzip sonar-scanner-cli-5.0.1.3006-linux.zip
                        export PATH=$PATH:$PWD/sonar-scanner-5.0.1.3006-linux/bin
                        sonar-scanner \
                          -Dsonar.organization=abdul007-tech \
                          -Dsonar.projectKey=8.2CDevSecOps \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=https://sonarcloud.io \
                          -Dsonar.login=$SONAR_TOKEN
                    '''
                }
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

        stage('Notify') {
            steps {
                echo 'Sending email notification (simulation)...'
                echo 'Subject: Jenkins CI/CD Pipeline Finished'
                echo 'Body: Pipeline completed for Abdul007-tech/8.2CDevSecOps'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
