pipeline {
    agent any

    environment {
        // Define environment variables
        DEPLOYMENT_PATH = '/path/to/deployment'
    }

    stages {

        stage('Build') {
            steps {
                bat 'dotnet restore'
                bat 'dotnet build --configuration Release'
                bat 'dotnet publish -c Release -o published'
                archiveArtifacts artifacts: 'published/**/*', fingerprint: true
            }
        }

        stage('Test') {
            steps {
                echo 'RUNNING TEST'
            }
            post {

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

    post {

    }
}
