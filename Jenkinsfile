pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "home/usr/src"
        STAGING_ENVIRONMENT = "GCP Google Kubernetes Engine Cluster"
        PRODUCTION_ENVIRONMENT = "GCP Google Kubernetes Engine Cluster"
    }
    stages {
        stage('BUILD') {
            steps {
                echo "fetch the source code from the directory path: $DIRECTORY_PATH"
                echo "build project using maven"
                echo "build complete"
            }
        }
        stage('UNIT & INTEGRATION TEST') {
            steps {
                echo "run unit tests using JUnit"
                echo "run integration tests using Selenium"
                echo "tests pass"
            }
        }
        stage('CODE ANALYSIS') {
            steps{
                echo "check the quality of the code using Checkstyle"
                echo "check complete"
            }
        }
        stage('SECURITY SCAN') {
            steps{
                echo "perform code security scan using SNYK"
                echo "scanned, no vulnerabilities found"
            }
        }
        stage('DEPLOY TO STAGING') {
            steps{
                echo "deploy the application to a staging environment: $STAGING_ENVIRONMENT"
                echo "deployed to staging successfully"
            }
        }
        stage('INTEGRATION TEST ON STAGING') {
            steps{
                echo "integration test using Selenium on staging server"
                echo "tests pass"
            }
        }
        stage('DEPLOY TO PRODUCTION') {
            steps{
                echo "deploy the code to the production environment: $PRODUCTION_ENVIRONMENT"
                echo "deployed successfully"
            }
            post{
                success{
                    emailext attachLog: true, body: '', subject: '', to: 'cjvirdo@gmail.com'
                }
            }
        }
    }
}
