pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "home/usr/src"
        TESTING_ENVIRONMENT = "testenv"
        PRODUCTION_ENVIRONMENT = "christians environment"
    }
    stages {
        stage('BUILD') {
            steps {
                echo "fetch the source code from the directory path: $DIRECTORY_PATH"
                echo "compile the code and generate any necessary artifacts"
            }
        }
        stage('TEST') {
            steps {
                echo "unit tests"
                echo "integration tests"
            }
        }
        stage('CODE QUALITY CHECK') {
            steps{
                echo "check the quality of the code"
            }
        }
        stage('DEPLOY') {
            steps{
                echo "deploy the application to a testing environment: $TESTING_ENVIRONMENT"
            }
        }
        stage('APPROVAL') {
            steps{
                echo "waiting for approval"
                sleep 10
                echo "approved"
            }
        }
        stage('DEPLOY AND PRODUCTION') {
            steps{
                echo "deploy the code to the production environment: $PRODUCTION_ENVIRONMENT"
                echo "testing github trigger"
            }
        }
    }
}
