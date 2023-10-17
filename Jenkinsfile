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
