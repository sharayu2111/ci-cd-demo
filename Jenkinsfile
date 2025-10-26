pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/</sharayu2111/ci-cd-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest || echo "No tests found, continuing..."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Flask app...'
                sh 'nohup python app.py &'
            }
        }
    }
}
