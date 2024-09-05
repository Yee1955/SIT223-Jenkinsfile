pipeline {
    agent any
    
    environment {
        // Define environment variables
        DEPLOYMENT_PATH = '/path/to/deployment'
    }

    stages {

        stage('Install dependencies') {
            steps {
                script {
                    // Use a Node.js Docker image to install dependencies
                    docker.image('node:16').inside {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the application
                    docker.image('node:16').inside {
                        sh 'npm run build' // Make sure your package.json includes a "build" script
                    }
                }
            }
        }

        stage('Test') {
            steps {
                echo 'RUNNING TEST'
                script {
                    // Run tests
                    docker.image('node:16').inside {
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'RUNNING DEPLOY'
            }
        }

        stage('Release') {
            steps {
                echo 'RUNNING RELEASE'
            }
        }

    }
}
