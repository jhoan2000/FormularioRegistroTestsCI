pipeline {
    agent any

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
                bat 'dotnet build --configuration Release --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }

        stage('Deploy Simulation') {
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
