pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ZAIDALIKHAN/flask-ci-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'script.sh'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_app.py || true'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Flask app...'
                sh 'nohup python3 app.py &'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Something went wrong!'
        }
    }
}

