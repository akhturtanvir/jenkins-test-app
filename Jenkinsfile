pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yourusername/your-repo.git'
            }
        }

        stage('Deploy to Local Server') {
            steps {
                echo "==== Deploying Website to Local Server ===="

                sh '''
                    TARGET_DIR="/var/www/html/app2"

                    # Create target folder if it doesn't exist
                    sudo mkdir -p $TARGET_DIR

                    # Copy everything from workspace to server directory
                    sudo rsync -avz --delete $WORKSPACE/ $TARGET_DIR/

                    # Fix permissions so Apache/Nginx can read files
                    sudo chown -R www-data:www-data $TARGET_DIR/

                    echo "==== Deployment Completed Successfully ===="
                '''
            }
        }
    }

    post {
        success {
            echo "🎉 Deployment finished successfully!"
        }
        failure {
            echo "❌ Deployment failed!"
        }
    }
}
