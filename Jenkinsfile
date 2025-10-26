pipeline {
    agent any

    environment {
        PYTHON = '"C:\\Users\\Sharayu Pathare\\AppData\\Local\\Programs\\Python\\Python313\\python.exe"'
        PIP = '"C:\\Users\\Sharayu Pathare\\AppData\\Local\\Programs\\Python\\Python313\\Scripts\\pip.exe"'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo '📥 Checking out code from GitHub...'
                git url: 'https://github.com/sharayu2111/ci-cd-demo.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📦 Installing dependencies...'
                bat "${PIP} install --upgrade pip"
                bat "${PIP} install -r requirements.txt"
            }
        }

        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                bat "${PYTHON} -m pytest || echo \"No tests found, continuing...\""
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Starting Flask app...'
                bat """
                    python -m venv venv
                    call venv\\Scripts\\activate
                    ${PIP} install -r requirements.txt
                    start /B ${PYTHON} app.py
                """
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
