pipeline {
    agent any

    environment {
        APP_NAME = 'my-app'
        BUILD_DIR = 'build'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                git 'https://github.com/harishvaka/demo.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the application
                    echo "Building the application"
                    sh 'export MAVEN_HOME=/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven/'
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run unit tests
                    echo "Running unit tests"
                    sh 'mvn test'
                }
            }
        }

    }

    post {
        success {
            // Actions to perform after a successful pipeline run
            echo 'Pipeline completed successfully!'
        }
        failure {
            // Actions to perform if the pipeline fails
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}

