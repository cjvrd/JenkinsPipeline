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
            }
            post{
                success{
                    emailext attachLog: true, body: 'Initial Unit and Integration Tests Pass', subject: 'PIPELINE STATUS', to: 'cjvirdo@gmail.com'
                }
                failure{
                    emailext attachLog: true, body: 'Initial Unit and Integration Tests Failed', subject: 'PIPELINE STATUS', to: 'cjvirdo@gmail.com'
                }
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
            }
            post{
                success{
                    emailext attachLog: true, body: 'Security Scan Pass, No Vulnerabilities Found', subject: 'PIPELINE STATUS', to: 'cjvirdo@gmail.com'
                }
                failure{
                    emailext attachLog: true, body: 'Security Scan Failed, Vulnerabilities Found', subject: 'PIPELINE STATUS', to: 'cjvirdo@gmail.com'
                }
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
            }
            post{
                success{
                    emailext attachLog: true, body: 'Integration Tests in Staging Pass', subject: 'PIPELINE STATUS', to: 'cjvirdo@gmail.com'
                }
                failure{
                    emailext attachLog: true, body: 'Integration Tests in Staging Failed', subject: 'PIPELINE STATUS', to: 'cjvirdo@gmail.com'
                }
            }
        }
        stage('DEPLOY TO PRODUCTION') {
            steps{
                echo "deploy the code to the production environment: $PRODUCTION_ENVIRONMENT"
                echo "deployed successfully"
            }
        }
    }
}
