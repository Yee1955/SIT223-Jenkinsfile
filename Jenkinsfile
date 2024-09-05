pipeline {
    agent any
    
    tools {
        // This should reference the .NET SDK you've configured under Global Tool Configuration in Jenkins
        dotnetsdk 'DotNet6' // Replace 'DotNet6' with the name of your .NET SDK installation
    }
    
    environment {
        // Define environment variables
        DEPLOYMENT_PATH = '/path/to/deployment'
    }

    stages {

        stage('Build') {
            steps {
                sh 'dotnet restore'
                sh 'dotnet build --configuration Release'
                sh 'dotnet publish -c Release -o published'
                archiveArtifacts artifacts: 'published/**/*', fingerprint: true
            }
        }

        stage('Test') {
            steps {
                echo 'RUNNING TEST'
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
