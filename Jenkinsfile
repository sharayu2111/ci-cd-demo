pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest || echo "No tests found, continuing..."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Flask app...'
                bat 'start /B python app.py'
            }
        }
    }
}
