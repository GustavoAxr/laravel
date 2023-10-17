pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'composer install'
            }
        }

        stage('Prepare Environment') {
                steps {
            // Copia la plantilla .env.example como .env
                bat 'copy .env.example .env'
        }
    }

        stage('Generate Application Key') {
            steps {
                bat 'php artisan key:generate'
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat 'php artisan test'
            }
        }
    }

    post {
        always {
            junit '**/junit.xml'
        }
    }
}
