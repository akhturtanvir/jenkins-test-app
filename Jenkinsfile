pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/akhturtanvir/jenkins-test-app.git'
            }
        }

        stage('Clean old files') {
            steps {
                sh '''
                    sudo rm -rf /var/www/html/*
                '''
            }
        }

        stage('Deploy HTML Files') {
            steps {
                sh '''
                    sudo cp -r * /var/www/html/app2
                '''
            }
        }

    }

    post {
        success {
            echo "HTML site deployed successfully on local machine!"
        }
    }
}
