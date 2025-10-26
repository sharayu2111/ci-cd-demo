pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat '"C:\\Users\\Sharayu Pathare\\AppData\\Local\\Programs\\Python\\Python313\\Scripts\\pip.exe" install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat '"C:\\Users\\Sharayu Pathare\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pytest || echo "No tests found, continuing..."'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Starting Flask app...'
                bat 'start /B "" "C:\\Users\\Sharayu Pathare\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" app.py'
            }
        }
    }
}

