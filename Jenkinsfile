pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/FCID-NHE/jenkins-laravel.git'
                sh 'composer install'
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
            }
        }
        stage('Test') {
            steps {
                sh 'ssh yoda@10.10.10.10 "docker-compose up -d"' 
                sh './vendor/bin/phpunit'
            }
        }
    }
}
