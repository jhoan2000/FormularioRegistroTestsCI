pipeline {
    agent any

    environment {
        CONFIGURATION = 'Release'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/jhoan2000/FormularioRegistroTestsCI.git'
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat "dotnet build --configuration %CONFIGURATION% --no-restore"
            }
        }

        stage('Test') {
            steps {
                bat "dotnet test --no-build --configuration %CONFIGURATION% --verbosity normal"
            }
        }

        stage('Deploy Simulation') {
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            steps {
                echo 'Simulando despliegue...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed.'
        }
    }
}
