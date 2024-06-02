pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "home/usr/src"
        STAGING_ENVIRONMENT = "stag env"
        PRODUCTION_ENVIRONMENT = "prod env"
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
                echo "check the quality of the code"
            }
        }
        stage('SECURITY SCAN') {
            steps{
                echo "scan"
            }
        }
        stage('DEPLOY TO STAGING') {
            steps{
                echo "deploy the application to a staging environment: $STAGING_ENVIRONMENT"
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
            }
            post{
                success{
                    mail to: "cjvirdo@gmail.com",
                    subject: "Build Status Email",
                    body: "Deployed Successfully",
                }
            }
        }
    }
}
