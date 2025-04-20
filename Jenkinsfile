/* 

pipeline {
    agent {
    
        label 'slave-1'
    }
    tools {
        maven 'Maven 3.9.9'
    }

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
*/

pipeline {
    agent {
        label 'slave-1'
    }

    environment {
        APP_NAME = 'my-app'
        BUILD_DIR = 'build'
    }

    stages {
        stage('Checkout & Build in Container') {
            steps {
                script {
                    docker.image('maven:3.9-eclipse-temurin-17').inside {
                        // Checkout code inside the container
                        git 'https://github.com/harishvaka/demo.git'

                        // Build the application
                        echo "Building the application"
                        sh 'mvn clean install'

                        // Run unit tests
                        echo "Running unit tests"
                        sh 'mvn test'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
