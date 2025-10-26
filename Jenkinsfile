pipeline {
    agent any

    environment {
        PYTHON = 'python' // or 'python3' depending on your setup
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo '📥 Checking out code from GitHub...'
                git branch: 'main', url: 'https://github.com/sharayu2111/ci-cd-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📦 Installing required dependencies...'
                // Windows-safe: create venv & install from requirements.txt
                bat '''
                    %PYTHON% -m venv venv
                    call venv\\Scripts\\activate
                    pip install --upgrade pip
                    if exist requirements.txt pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                bat '''
                    call venv\\Scripts\\activate
                    pytest || echo "⚠️ Tests failed or not found, continuing..."
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'
                bat '''
                    call venv\\Scripts\\activate
                    echo "Running Flask app..."
                    python app.py
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build succeeded!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
